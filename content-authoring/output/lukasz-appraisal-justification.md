# Lukasz Kowalczyk — Appraisal Justification: Exceeds Expectations (L2)

## Knowledge and Experience

**Exceeds expectations:** The L2 bar asks for independent working and the ability to tackle complicated problems. Translating "Proficient in main programming language in a project and knows corresponding technologies" to mean core technologies for DevOps. Looking at what Lukasz has actually delivered this year, he's well beyond just core tech. He's had significant contribution on several high-impact deliverables:

- **Ephemeral environments (Zephyr):** Configured at least 12 services for ephemeral deployment from scratch, plus Karpenter node pools, Redis/ReJSON, QA-SIT database snapshot, image-updater, and eph-zero application spec.
- **Argo Rollouts:** Implemented "Fast" and "Slow" deployment configurations and drove broader rollout adoption.
- **Developer tooling:** GitHub-Slack integration, Slack-ops/Jira integration, Dependabot auto-merge workflow, Codacy repository automation, helm chart build workflow, Testcontainers upgrade, Gitstream AI enablement, deployment notifications template, Golang service scaffold.
- **Monitoring and observability:** Datadog sidecar for WireMock pods, Datadog source code integration.
- **API Gateway and security:** Public API Gateway security review and remediation, stage variable configuration, velocity-service migration.
- **Infrastructure operations:** SNS topic mapping, AWS parameter cleanup, ALBC helm chart upgrade, Aurora DB cleanup, ECR repo provisioning.

### References

| Area | Tickets |
|---|---|
| Ephemeral environments | ZILCH-41705 through ZILCH-41721, ZILCH-46719, ZILCH-39971, ZILCH-45432, ZILCH-46673, ZILCH-47382, ZILCH-47185 |
| Argo Rollouts | ZILCH-29213 |
| Developer tooling | ZILCH-43431, ZILCH-41181, ZILCH-45498, ZILCH-39121, ZILCH-39436, ZILCH-38471, ZILCH-46217, ZILCH-37617, ZILCH-35193 |
| Monitoring and observability | ZILCH-31485, ZILCH-38382 |
| API Gateway and security | ZILCH-32599, ZILCH-32603, ZILCH-32824, ZILCH-36429 |
| Infrastructure operations | ZILCH-38609, ZILCH-33076, ZILCH-44595, ZILCH-40209 |
| DEVOPS board (support) | DEVOPS-3, DEVOPS-9, DEVOPS-10, DEVOPS-13, DEVOPS-25, DEVOPS-34, DEVOPS-35, DEVOPS-45 |

### L3 Knowledge and Experience Gap Analysis

**Already evidenced:**
- *Works without supervision* — clearly demonstrated by the breadth and independence of his delivery across the year.
- *Able to solve complex problems* — the Zephyr/ephemeral environment work is technically complex and required judgement across multiple interacting systems.
- *Contributes to SDLC optimisation* — Argo Rollouts, quality gates, and the developer tooling programme all directly improve the SDLC.
- *Delivers across the entire tech stack* — evidenced across a wide range of technologies.

**Partially evidenced:**
- *Drives tech stack definition/changes* — some evidence through tooling choices, but not yet at a level that suggests he is driving those decisions rather than contributing to them.
- *Contributes to design and architecture, spots areas for improvement* — the environment locking spike (ZILCH-45416) and SQS/SNS Kubernetes operators investigation (ZILCH-36410) suggest this capacity, but it is not yet a consistent pattern.

**Not yet evidenced:**
- *Can decompose high-level requirements into detailed PBIs in collaboration with PdM* — DevOps work is largely self-directed rather than PM-collaborative; this may not be directly applicable.
- *Is an expert reviewer and teacher/mentor in software craftsmanship*
- *Understands and uses testing pyramid, influences quality improvements* — quality gates work is adjacent but not direct evidence.
- *Co-creates goals for the team, ensures accountability*

Knowledge and experience is Lukasz's strongest dimension and the L3 bar is within reach. The main development areas are around driving rather than contributing to architectural and stack decisions, and deepening influence on quality practices.

## Soft Skills

**Meets/exceeds expectations:** L2 specifies building relationships within the organisation and keeping people informed. Lukasz is well-regarded across the organisation as someone people turn to for help. He's been active in `#tech-devops` and `#platypus` throughout the year — unblocking deployments, resolving ArgoCD and pod issues, advising on architecture decisions (API Gateway → SQS → Lambda, Datadog configuration, Terraform workspace management), and reviewing infrastructure PRs. He often shows up in those channels as cheerfully helpful with a can-do attitude. He's also worked closely with QA engineers on quality gate configuration. There's a bit of a gap for L3 skill set — as detailed in my appraisal write-up.

### L3 Soft Skills Gap Analysis

**Already evidenced:**
- *Builds effective relationships across organisations* — cross-team channel presence demonstrates this clearly.
- *Has impact on other teams* — deployment support and architecture guidance in `#tech-devops` directly unblocks other teams.
- *Always aware of context and keeps others informed* — consistent with how he operates in support channels.

**Partially evidenced:**
- *Manages obstacles* — reactive support work shows this, but more "resolves when asked" than proactively anticipating and heading things off.

**Not yet evidenced:**
- *Leverages external relationships to ensure on-time delivery*
- *Shows ownership of delivering results beyond the team/product* — channel support is reactive rather than ownership-driven.
- *Leads the team towards meeting goals*
- *Leverages team members' strengths and weaknesses in planning and executing*

The cross-organisational relationship-building and cross-team impact are genuine L3 traits and justify "meets/exceeds". The gaps — proactive ownership and leading others — are natural development themes for his L3 year.

## Growth Potential

**Exceeds expectations:** The L2 bar asks for self-awareness and a willingness to step outside your comfort zone. Lukasz came into the year knowing he had ground to make up and made it up largely on his own initiative — no one needed to push him. See appraisal write-up for detail.

### L3 Growth Potential Gap Analysis

**Already evidenced:**
- *Volunteers to opportunities outside his regular role* — consistent across the year; on-call participation, cross-team support, quality gates work with QA.
- *Shows curiosity towards technology, keeps track of trends* — evidenced by his self-directed learning and interest in Zoe/Golang.
- *Has a plan for career progression* — clear and specific, articulated in self-appraisal.

**Partially evidenced:**
- *Comes up with improvement initiatives, able to identify problematic areas* — the developer tooling work (integrations, workflows, scaffold) suggests this, though it's hard to distinguish self-initiated from directed.
- *Uses data in day-to-day work to understand his context* — not directly evidenced, but his interest in team metrics and LinearB access request suggests awareness.

**Not yet evidenced:**
- *Looks beyond his goals to organisational and product goals; helps connect them to vision, mission and strategy*
- *Actively looks for improvements to his project's/product's stack* — some tooling work hints at this but not clearly ownership-driven.
- *Considers different plans for career and keeps options open*

The self-directed growth arc is a strong L3 indicator. The gaps are around strategic awareness and connecting personal work to organisational goals — natural themes for his L3 year.

## Leadership

**Meets expectations:** Where the requirements for the L2 Leadership section apply, Lukasz meets them. (Some do not apply: e.g. interviewing candidates.)

He's mentoring less experienced colleagues — though it's worth being clear that I interpret this to mean software engineers who may be more experienced in their own domain, but less experienced in the DevOps domain. Through `#tech-devops`, Lukasz has been a go-to resource for engineers across the organisation on CI/CD, deployment workflows, and testing practices.

I have no evidence for him effectively creating transparent plans, but I am more than happy that he meets expectations in this category on the strength of other measures such as "Actively seeks to understand others and their point of view" and "Relentless learner".

### L3 Leadership Gap Analysis

**Already evidenced:**
- *Understands vision, mission and strategy and how they correlate with goals* — his self-appraisal and focus on roadmap-aligned work suggests this.
- *Relentless learner* — well evidenced throughout.
- *Acts as buddy/mentor for new hires and less experienced colleagues* — informally, through channel support.

**Not yet evidenced:**
- *Actively contributes to strategy and goals refinement* — no evidence of this yet.
- *Creates plans for different scenarios* — no evidence.
- *Acts as role model for others; makes others better* — too early to say at this stage.
- *Contributes to onboarding plan improvements*
- *Skilled interviewer* — no evidence of interview involvement.

Leadership is the clearest area of development for his L3 year. The channel support shows early instincts but he needs to move from reactive helpfulness to active enablement and influence.

---

Nominated for promotion to L3.
