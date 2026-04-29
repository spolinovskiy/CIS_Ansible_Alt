# Passwords Chapter Report (ALT-1008)

## Scope
- Project: ALT Linux CIS Ansible for OT
- PRD task: ALT-1008
- Sheet/chapter: Passwords
- Control rows implemented: 5.4.1.1, 5.4.1.2, 5.4.1.3, 5.4.1.4, 5.4.1.5, 5.4.1.6
- Group header rows implemented: none (intentionally excluded)

## Status Buckets
- implemented: 5.4.1.1, 5.4.1.2, 5.4.1.3, 5.4.1.4, 5.4.1.5, 5.4.1.6
- skipped: none
- manual: 5.4.1.2
- blocked: none
- high-risk: 5.4.1.1, 5.4.1.2, 5.4.1.3, 5.4.1.4, 5.4.1.5, 5.4.1.6

## Audit and Safety Assumptions
- Audit-only behavior is the default; remediation is not implemented in this task.
- All Passwords tasks are read-only and use `changed_when: false`.
- No Internet dependencies are introduced.
- No password policy remediation or account modifications are executed.

## Missing Information Placeholders (Policy Baselines)
- `MISSING_OT_BASELINE:approved_min_password_days_threshold`
- `MISSING_OT_BASELINE:approved_password_hashing_algorithms`
- `MISSING_OT_BASELINE:approved_inactive_lock_threshold`
- `MISSING_OT_BASELINE:approved_last_password_change_exceptions`

## OS Tested
- Local implementation validation host: macOS workstation used for repository work.
- Target ALT runtime testing: not executed in this workstation task.
- Runtime target facts are captured under `cis_passwords_chapter.os_tested` during play execution.

## Commands Implemented (Audit Evidence Collection)
- `awk` checks on `/etc/login.defs` for PASS_MAX_DAYS, PASS_MIN_DAYS, PASS_WARN_AGE
- `grep` checks for hashing algorithm configuration in `/etc/login.defs` and `/etc/pam.d`
- `awk` check for `INACTIVE` in `/etc/default/useradd`
- `awk` check for future password change dates in `/etc/shadow`

## Evidence Records (Registered Outputs)
- `cis_5_4_1_1_pass_max_days`
- `cis_5_4_1_2_pass_min_days`
- `cis_5_4_1_3_pass_warn_age`
- `cis_5_4_1_4_hashing_algo`
- `cis_5_4_1_5_inactive_days`
- `cis_5_4_1_6_future_last_change`
- Aggregated chapter evidence: `cis_passwords_chapter.evidence_records`

## Result Summary
- Per-control runtime status is aggregated into `cis_passwords_chapter.result_summary`.
- Policy-dependent controls use `manual_review_required` until approved thresholds/exception baselines are provided.

ENGINEER APPROVAL REQUIRED BEFORE FINAL COMPLETION.
