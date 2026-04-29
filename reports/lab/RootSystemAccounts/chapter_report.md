# Root&System Accounts Chapter Report (ALT-1009)

## Scope
- Project: ALT Linux CIS Ansible for OT
- PRD task: ALT-1009
- Sheet/chapter: Root&System Accounts
- Control rows implemented: 5.4.2.1, 5.4.2.2, 5.4.2.3, 5.4.2.4, 5.4.2.5, 5.4.2.6, 5.4.2.7, 5.4.2.8, 5.4.3.1, 5.4.3.2, 5.4.3.3
- Group header rows implemented: none (intentionally excluded)

## Status Buckets
- implemented: 5.4.2.1, 5.4.2.2, 5.4.2.3, 5.4.2.4, 5.4.2.5, 5.4.2.6, 5.4.2.7, 5.4.2.8, 5.4.3.1, 5.4.3.2, 5.4.3.3
- skipped: none
- manual: 5.4.2.5, 5.4.2.7, 5.4.2.8, 5.4.3.2, 5.4.3.3
- blocked: none
- high-risk: 5.4.2.1, 5.4.2.2, 5.4.2.3, 5.4.2.4, 5.4.2.5, 5.4.2.6, 5.4.2.7, 5.4.2.8, 5.4.3.1, 5.4.3.2, 5.4.3.3

## Audit and Safety Assumptions
- Audit-only behavior is enforced; no remediation actions are implemented in this task.
- All Root&System Accounts tasks are read-only and use `changed_when: false`.
- No Internet dependencies are introduced.
- No account locks/unlocks, shell changes, PATH/profile edits, or privilege modifications are executed.

## Missing Information Placeholders (Policy Baselines)
- `MISSING_OT_BASELINE:approved_system_uid_max`
- `MISSING_OT_BASELINE:approved_root_gid0_account_exceptions`
- `MISSING_OT_BASELINE:approved_gid0_group_exceptions`
- `MISSING_OT_BASELINE:approved_root_path_exceptions`
- `MISSING_OT_BASELINE:approved_root_umask_patterns`
- `MISSING_OT_BASELINE:approved_system_shell_exceptions`
- `MISSING_OT_BASELINE:approved_non_login_unlocked_exceptions`
- `MISSING_OT_BASELINE:approved_tmout_max_seconds`
- `MISSING_OT_BASELINE:approved_default_umask_patterns`

## OS Tested
- Local implementation validation host: macOS workstation used for repository work.
- Target ALT runtime testing: not executed in this workstation task.
- Runtime target facts are captured under `cis_root_system_accounts_chapter.os_tested` during play execution.

## Commands Implemented (Audit Evidence Collection)
- `awk` checks on `/etc/passwd`, `/etc/group`, `/etc/shadow`, `/etc/login.defs`
- `passwd -S root`
- `grep` checks on `/etc/shells`, `/etc/profile*`, `/etc/bash*`, and root shell init files
- `stat` checks for root PATH directory ownership and permissions

## Evidence Records (Registered Outputs)
- `cis_5_4_2_1_uid0_accounts`
- `cis_5_4_2_2_gid0_accounts`
- `cis_5_4_2_3_gid0_groups`
- `cis_5_4_2_4_root_passwd_status`
- `cis_5_4_2_5_root_path_integrity`
- `cis_5_4_2_6_root_umask`
- `cis_5_4_2_7_system_valid_shells`
- `cis_5_4_2_8_non_login_not_locked`
- `cis_5_4_3_1_nologin_in_shells`
- `cis_5_4_3_2_tmout_config`
- `cis_5_4_3_3_default_umask`
- Aggregated chapter evidence: `cis_root_system_accounts_chapter.evidence_records`

## Result Summary
- Per-control runtime status is aggregated into `cis_root_system_accounts_chapter.result_summary`.
- Policy-dependent controls use `manual_review_required` until approved OT baselines are provided.

ENGINEER APPROVAL REQUIRED BEFORE FINAL COMPLETION.
