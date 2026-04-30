# SERVICES Chapter Report (ALT-1016)

## Scope
- Project: ALT Linux CIS Ansible for OT
- PRD task: ALT-1016
- Sheet/chapter: SERVICES
- Control rows implemented: 2.1.1, 2.1.2, 2.1.3, 2.1.4, 2.1.5, 2.1.6, 2.1.7, 2.1.8, 2.1.9, 2.1.10, 2.1.11, 2.1.12, 2.1.13, 2.1.14, 2.1.15, 2.1.16, 2.1.17, 2.1.18, 2.1.19, 2.1.20, 2.1.21, 2.1.22, 2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.2.6
- Group header rows implemented: none (intentionally excluded; scope locked to control rows from linux_cis.xlsx SERVICES sheet, including excluded headers 2.1 and 2.2)

## Status Buckets
- implemented: 2.1.1, 2.1.2, 2.1.3, 2.1.4, 2.1.5, 2.1.6, 2.1.7, 2.1.8, 2.1.9, 2.1.10, 2.1.11, 2.1.12, 2.1.13, 2.1.14, 2.1.15, 2.1.16, 2.1.17, 2.1.18, 2.1.19, 2.1.20, 2.1.21, 2.1.22, 2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.2.6
- skipped: none
- manual: 2.1.20, 2.1.21, 2.1.22, 2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.2.6
- blocked: runtime-derived from `cis_services_chapter.result_summary`
- high-risk: 2.1.1, 2.1.2, 2.1.3, 2.1.4, 2.1.5, 2.1.6, 2.1.7, 2.1.8, 2.1.9, 2.1.10, 2.1.11, 2.1.12, 2.1.13, 2.1.14, 2.1.15, 2.1.16, 2.1.17, 2.1.18, 2.1.19, 2.1.20, 2.1.21, 2.1.22, 2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.2.6

## Audit and Safety Assumptions
- Audit-only behavior is implemented; no remediation actions are present.
- All audit checks are read-only and use `changed_when: false`.
- No Internet dependencies are introduced.
- No stop/disable/restart/reload/reboot operations are performed.

## Missing Information Placeholders (OT Baselines)
- `MISSING_OT_BASELINE:approved_service_allowlist`
- `MISSING_OT_BASELINE:approved_listening_services_and_ports`
- `MISSING_OT_BASELINE:approved_mta_local_only_policy`
- `MISSING_OT_BASELINE:approved_client_package_exceptions`

## OS Tested
- Local implementation validation host: macOS workstation used for repository work.
- Target ALT runtime testing: not executed in this workstation task.
- Runtime target facts are captured under `cis_services_chapter.os_tested` during play execution.

## Commands Implemented (Audit Evidence Collection)
- Commands are defined per-control in `cis_services_controls[*].command`.
- Aggregated command inventory is exposed in `cis_services_chapter.commands`.

## Evidence Records (Registered Outputs)
- `cis_services_control_evidence`
- Aggregated chapter evidence: `cis_services_chapter.evidence_records`

## Result Summary
- Per-control runtime status is aggregated into `cis_services_chapter.result_summary`.
- Statuses are computed as `pass/fail/blocked/manual_review_required` without making host changes.

## Temporary/Default Baseline Notes
- Service allowlist, listening services/ports baseline, MTA local-only policy, and client-package exceptions remain placeholders until environment-approved OT baselines are provided.

ENGINEER APPROVAL REQUIRED BEFORE FINAL COMPLETION.
