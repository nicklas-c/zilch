# Instrument `acquisition-tracking` for Grafana

**Parent epic:** ZILCH-58278

## Goal

`acquisition-tracking` sends traces and metrics to Grafana Cloud via the OTel gateway, while continuing to send to Datadog.

## Work

1. **Traces** — Configure `acquisition-tracking` to export OTel traces through the gateway, following the approach from ZILCH-57170.
2. **Metrics** — Add `micrometer-registry-otlp` to `acquisition-tracking` per the pattern in ZILCH-58309.  Verify metrics appear in both Grafana and Datadog.
3. **Validation** — Confirm traces and metrics are visible in Grafana Cloud on an eph environment.  Flag any tag mismatches or missing data.

## Risks

- Datadog tags differ between DogStatsD and OTLP paths — see ZILCH-58309 risks section.
- `micrometer-registry-otlp` version must match the service's Micrometer version.

## References

- ZILCH-57170 — Trace agent investigation (Done)
- ZILCH-58309 — Metrics OTLP migration
