# Attack Surface Reduction (ASR) - Threat Hunting (MDE)

This folder contains **advanced hunting queries** focused on visibility, effectiveness,
and investigation of **Attack Surface Reduction (ASR)** events in Microsoft Defender
for Endpoint (MDE).

These queries are designed to support:
- **Control validation** (are ASR rules firing where expected?)
- **Noise vs signal separation** (what is benign vs suspicious?)
- **Investigation workflows** (quick pivots from rule → device → process → hash)

> Telemetry note: ASR events may be recorded under `DeviceEvents` with `ActionType`
> values related to ASR. Some environments capture richer ASR metadata inside
> `AdditionalFields` (JSON). Each query states assumptions and can be adapted.

---

## Hunting Objectives

- Identify **top triggered rules** and rule trends over time
- Detect **rare / high-signal ASR triggers**
- Correlate ASR triggers with **binaries, paths, and initiating processes**
- Identify devices with **unusual ASR activity** (possible misconfig or attack)
- Provide **investigation pivots** that are repeatable and explainable

---

## Operational Notes

- High trigger counts are not inherently malicious. They often indicate:
  - aggressive rules + noisy apps
  - new rollout, audit-to-block transition
  - software deployment events
- Treat **rare triggers**, **new binaries**, **unusual paths**, and **clusters** as higher signal.
- Prefer tuning by:
  - limiting known-good publishers / signed binaries
  - scoping by device group/role
  - suppressing stable, well-understood benign patterns
- Avoid “exception sprawl”. Track exclusions as **policy changes** with review.

---

## Query List

- `asr-events-count-by-rule.kql` - Rule trigger distribution + trend
- `asr-top-triggered-rules.kql` - Top rules with optional rule mapping support
- `asr-rare-rule-triggers.kql` - Rare rules / rare devices (high signal)
- `asr-filename-rule-correlation.kql` - Binaries and paths associated with ASR triggers
- `asr-devices-with-unusual-asr-volume.kql` - Outlier devices by ASR activity

---

## Suggested Investigation Pivots

When a suspicious ASR trigger is found:
1. Pivot to **initiating process lineage** (parent/child, command line)
2. Pivot to **hash prevalence** (rare hash, first seen)
3. Pivot to **device timeline** for surrounding events
4. Pivot to **network** (if relevant) for new outbound destinations
