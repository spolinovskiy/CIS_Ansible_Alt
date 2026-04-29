# Reporting Strategy

This document defines audit result output and tracking requirements for the ALT CIS project in an offline OT environment.

## Mandatory Outcomes

1. Each audit run must generate an automatic per-host checklist with status per CIS control from `linux_cis.xlsx`.
2. Results must be collated per machine in a machine-readable format suitable for aggregation and diffs.
3. Repeated audits must support change tracking versus previous runs.

## Built-in Ansible Options (Reference)

- `ansible.builtin.tree` callback: writes per-host JSON event files (good offline default).
- `ansible.builtin.junit` callback: writes JUnit XML output (CI-compatible XML).
- `ansible.posix.json` / `ansible.posix.jsonl` callbacks: structured JSON stdout output (requires collection availability).
- Fact cache plugins (`ansible.builtin.jsonfile`, `redis`) can persist host data for repeat comparisons.
- `ansible.builtin.set_stats` can publish run-level and per-host summary stats.

## Recommended Offline Baseline

- Primary format: JSON per host per run (stable schema).
- Optional exports: Markdown summary and CSV flattening for operators.
- Storage path: repository/local path under `reports/<env>/<timestamp>/` per run.

## Optional XML Mode (Not Mandatory)

- XML export can be enabled with built-in `ansible.builtin.junit` callback when `ansible-playbook` is available in the execution environment.
- This is an optional parallel output mode only; runtime must not depend on XML generation.
- Current workstation validation cannot execute this callback mode because `ansible-playbook` is not installed here.

## Database Storage (Future, Approval-Gated)

- No database dependency is introduced in the current baseline.
- Database-backed storage/analytics is a possible future enhancement only after explicit approval for the target industrial segment.

## Delta Tracking (Implemented)

- Baseline source selection per host:
  - First preference: `reports/lab/latest/<host>/checklist.json` (loaded before `latest` is overwritten).
  - Fallback: most recent timestamped `reports/lab/<run_id>/<host>/checklist.json` if `latest` does not exist.
  - If neither exists, baseline is `none` and all scoped controls are marked `new`.
- Per-host delta artifact:
  - Written as `delta.json` in both `reports/lab/<run_id>/<host>/` and `reports/lab/latest/<host>/`.
  - Includes baseline metadata, per-control previous/current status, and classification.
- Delta classification rules:
  - `new`: control absent in baseline host checklist.
  - `unchanged`: baseline status equals current status.
  - `resolved`: baseline status was not `pass` and current status is `pass`.
  - `changed`: any other status transition when baseline exists.
- Run-level delta summary:
  - Written as `run_delta_summary.json` in `reports/lab/<run_id>/` and `reports/lab/latest/`.
  - Aggregates `changed/new/resolved/unchanged` totals and per-control counts across all hosts.

## Scope and Safety

- Scope is locked to controls from `linux_cis.xlsx` only.
- No internet downloads or external services required for reporting/tracking baseline.
