**Date**: Friday, 28 August 2026 at 15:04
**To**: Steve Rayko <steve.rayko@payzilch.com>; David Ramsay <david.ramsay@payzilch.com>
**Cc**: Denis Greyling <denis.greyling@coralogix.com>; Assaf Shutan <assaf.sh@coralogix.com>; Ron Avnery <ron.avnery@coralogix.com>
**Subject**: Zilch & Coralogix Follow Up

Hi Steve, David,

Thanks for the time yesterday. Steve, good to finally meet. David, thanks again for liaising on the Zilch side to get us all connected.

Quick recap on what we heard: You are not spend-averse, you are value-averse. Datadog is Rolls-Royce money, and the question is whether the ride justifies the price. Observability can't be compromised, but trajectory, partnership, and share of wallet all need to add up. Feature parity first, then a pragmatic comparison against what you have today.

Where Coralogix fits:
- Cost and control: Ingest-based pricing only, with no per-seat, per-dashboard, or overage surprises. This model, coupled with our unique architecture, typically results in 40 to 70 percent lower TCO than any other tool in the market.
- Data ownership: Streama analyses, alerts, and detects anomalies in-stream on ingest, then lands data in your own S3 in open Parquet. Queryable in place via DataPrime, no rehydration, no index. Steve, on your question, a sub-second index query becomes a few seconds against S3, and where you need faster we can index a subset on our side should you require it.
- Coverage: Full stack in one platform, logs, metrics, traces, APM, RUM, AI, plus SIEM. OpenTelemetry front to back, 500+ integrations, no agent lock-in.
- AI - Olly reasons over all your telemetry for RCA, blast radius, and suggested fixes. AI Center adds evaluators and real-time guardrails (PII, prompt injection, hallucination, toxicity), plus token and code-agent ROI tracking. cx CLI lets your engineers query from the IDE.

Actions:
On pricing, to move to an accurate TCO and prepare the side-by-side vendor comparison Steve asked for, we would like to line up two things in parallel:
NDA - David, if you can send your NDA, this allows us to generate accurate pricing off the bat and covers us for the wider comparison work.
   2. Sizing sheet - Alongside the NDA, if you can kindly fill out the attached sizing sheet, this lets us map high-level volumes and the features currently used within Datadog, which feeds directly into the feature-by-feature comparison you requested.

Also worth highlighting, we can factor in volumes from any other platforms in use (AWS CloudWatch, self-hosted stacks, open-source logging or metrics tools, etc.), so that the pricing view reflects the full observability estate rather than Datadog alone.

A couple of other follow-ups from the call:
- Coralogix regions, as requested. AWS - Ohio, Oregon, Stockholm, Mumbai, Singapore. GCP - Iowa.
- Follow-up working session with a wider group from your side (platform, SRE) once you have had a chance to review the pricing and comparison, so we can go deeper on the areas that matter most for Zilch and scope a focused POC around those use cases rather than a generic one.

Here are some resources to look through: 
CLI: https://cli.coralogix.dev/
Curve case study: https://coralogix.com/case-studies/curve/
Coralogix for fintech: https://coralogix.com/solutions/fintech/

Please let me know if I have missed anything. Otherwise, I look forward to your response and speaking soon.

Best,
Alex