# Advanced Threat Hunting Queries (Microsoft Defender)

This repository contains a curated set of **advanced threat hunting queries**
written in **Kusto Query Language (KQL)** for **Microsoft Defender for Endpoint
(MDE) Advanced Hunting**.

The focus is on:
- High-signal hunting hypotheses
- Practical investigation workflows
- Environment-aware tuning guidance
- Repeatable, explainable analysis

Queries are organized by **security domain**, not by product UI.

---

## Domains Covered

- Attack Surface Reduction (ASR)
- Endpoint process execution
- Persistence mechanisms
- Defense evasion and tampering
- Credential abuse signals
- File system activity
- Lateral movement
- Outbound network activity
- Asset baselining and drift
- Incident investigation pivots

---

## How to Use

1. Choose a domain folder
2. Review the domain README for context and assumptions
3. Run the KQL queries in **Defender Advanced Hunting**
4. Tune results based on your environment and baseline

---

## Telemetry Notes

All queries are written for **Defender for Endpoint Advanced Hunting tables**.
Query availability depends on enabled telemetry and licensing.

Each query file documents the required tables. If a table is unavailable,
use the query as a reference hypothesis and adapt accordingly.

---

## Safety & Ethics

These queries are intended for **defensive threat hunting and detection
engineering** only. They do not include offensive techniques or guidance
for misuse.
