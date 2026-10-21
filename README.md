# Bare-Metal vs. VM Malware Analysis

Testing whether VM-aware/evasive malware still exhibits a detectable behavioral
gap between a free VM sandbox (CAPE) and a low-cost bare-metal environment,
using modern tools and currently circulating samples.

**No malware samples are included or distributed in this repository.**
Only hashes, logs, and analysis are stored here.

## Status
- Environments built, isolated, and validated (Milestone #1 complete, 10/19)
- 15 candidate samples sourced from MalwareBazaar and vetted with capa
- Execution in progress — targeting 8–10 final samples across 3+ families
- Milestone #2 (full execution, both environments): 11/9

## Environments
- **VM:** CAPE on Ubuntu Server (VMware Workstation) controlling a hardened
  Windows 10 guest, isolated VMnet, no bridged/NAT adapter during analysis.
- **Bare-metal:** Dell OptiPlex 7010, no Wi-Fi/Bluetooth hardware, PXE
  disabled, no Intel AMT (non-vPro CPU), re-imaged via checksum-verified
  Clonezilla before every run.

## Repo structure
- `docs/` — proposal, status reports, architecture diagram
- `setup/` — environment build steps, containment plan, tool hardening
- `calibration/` — Pafish/al-khaser baselines, containment test results
- `samples/` — hash log and discard log (no sample files)
- `runs/` — per-sample logs from both environments
- `analysis/` — comparison table and findings
- `scripts/` — pre-run checklist and verification scripts

## Methodology
See `setup/containment-plan.md` and `analysis/findings.md` (once populated)
for the comparison criteria and divergence rules.
