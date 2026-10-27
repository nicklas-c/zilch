# Replacing Datadog Cluster Agent & Sidecars with OTel-Native / Open-Source Components

## Current State

Deployed via ArgoCD ApplicationSets, Helm chart `DataDog/helm-charts` v3.160.1, config at
`projects/monitoring/datadog-cluster-agent/values/datadog-cluster-agent.yaml`, rolled out
progressively by `env_type` (dev/qa/eph → staging → devops; prod manual).

| Feature | Status | Disposition |
|---|---|---|
| Logs (node, `containerCollectAll`) | Enabled | Migrate → `filelogreceiver` DaemonSet |
| Logs (Fargate, sidecar via kubelet-proxy) | Enabled | Migrate → custom in-house receiver (no stock OTel equivalent) |
| APM/traces (agent port + OTLP already open) | Enabled | Migrate → OTel Collector OTLP receiver, dual export |
| Metrics (DogStatsD, custom KSM) | Enabled | Migrate → `statsdreceiver`/OTLP + `prometheusreceiver` on existing KSM |
| External metrics/HPA provider | Config present, **not actually used** | Remove config; KEDA if ever needed |
| Orchestrator Explorer | Enabled | Stays on DD agent short-term; **needs follow-up replatform plan** |
| NPM (network monitoring) | Enabled | Stays on DD agent short-term; **needs follow-up replatform plan** (candidate: Cilium/Hubble) |
| Admission controller (Fargate sidecar injection) | Enabled | Migrate → `opentelemetry-operator` sidecar-mode CR + annotations |
| CWS/SBOM/USM | Disabled | N/A |

No existing OTel infrastructure in repo — greenfield build.

## Target Architecture

**Dual-ship during migration**: OTel Collector → Datadog exporter (`datadogexporter`, reuse
existing `datadog-cluster-agent-api-secrets`) + OTel-native second backend (Coralogix or Grafana
Cloud, both accept standard OTLP — `otlpexporter`/`otlphttpexporter`, no vendor-specific exporter
component needed).

### Node-based workloads (EC2)

- `opentelemetry-operator` + DaemonSet `OpenTelemetryCollector`: `filelogreceiver` (logs, carry
  over current exclusions), `hostmetricsreceiver`, `kubeletstatsreceiver`
- Gateway/Deployment `OpenTelemetryCollector`: `k8s_cluster` receiver, `prometheusreceiver`
  (scrape existing custom KSM), OTLP receiver 4317/4318 (traces), `statsdreceiver` (DogStatsD
  compatibility)
- Resource sizing: sized fresh per role, not mirrored from DD agent — needs a sizing/load-test
  pass before rollout, not assumed from existing config

### Fargate workloads

- Metrics/traces: OTel Collector sidecar-mode via `opentelemetry-operator`, kubelet cAdvisor
  scraped through API server proxy (matches Datadog's own DDOT pattern, no gap)
- Logs: **DevOps team owns build** of custom in-house OTel receiver using `client-go`'s pod
  log-stream API (`kubectl logs` equivalent) — no stock OTel Collector Contrib receiver does this,
  confirmed via upstream receiver list review; even Datadog's own OTel distro falls back to AWS
  Fluent Bit+CloudWatch here. Keep that AWS path documented as a fallback if the custom build
  stalls.

### Admission Controller replacement

- Sidecar-mode `OpenTelemetryCollector` CR + `sidecar.opentelemetry.io/inject` annotation replaces
  DD's Fargate sidecar profile (annotation-driven, not label-selector — remap targeting from
  `agent.datadoghq.com/sidecar: fargate`)

### Traces — dual instrumentation strategy

- Phase 1: apps keep existing `dd-trace` libraries, redirected to OTel collector's OTLP endpoint
  (dd-trace speaks OTLP-compatible wire format into the collector) — zero app code changes upfront
- Phase 2: DevOps requests individual service teams migrate to native OTel SDKs on their own
  schedule — per-team backlog item, not a blocking migration gate

## Rollout Sequencing

1. Deploy OTel collectors alongside DD agent (no removal), same progressive RollingSync tiers
2. Verify parity per tier (log volume, trace counts, metric coverage) before disabling matching DD
   agent features
3. Shrink DD agent config incrementally: `logs.enabled`, `apm.portEnabled`, DogStatsD off once
   confirmed; remove dead `clusterAgent.metricsProvider.enabled` config now regardless (unused)
4. DD agent stays running for Orchestrator Explorer, NPM until their follow-up replatform plans
   land

## Follow-Up Work Items (beyond this phase)

- **Orchestrator Explorer replatform**: evaluate `k8s_cluster` receiver / k8s API metrics as
  OTel-native substitute
- **NPM replatform**: evaluate Cilium/Hubble or eBPF-based OSS alternative
- **Coralogix vs. Grafana Cloud**: final pick, non-blocking — both are drop-in OTLP endpoints,
  just needs a token/endpoint once decided
