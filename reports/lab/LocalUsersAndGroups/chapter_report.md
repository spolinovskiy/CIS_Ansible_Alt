# Local Users and Groups Chapter Report (ALT-1006)

## Scope
- Project: ALT Linux CIS Ansible for OT
- PRD task: ALT-1006
- Sheet/chapter: Local Users and Groups
- Control rows implemented: 7.2.1, 7.2.2, 7.2.3, 7.2.4, 7.2.5, 7.2.6, 7.2.7, 7.2.8, 7.2.9, 7.2.10
- Group header rows implemented: none (intentionally excluded)

## Status Buckets
- implemented: 7.2.1, 7.2.2, 7.2.3, 7.2.4, 7.2.5, 7.2.6, 7.2.7, 7.2.8, 7.2.9, 7.2.10
- skipped: none
- manual: 7.2.9, 7.2.10
- blocked: none
- high-risk: 7.2.1, 7.2.2, 7.2.3, 7.2.4, 7.2.5, 7.2.6, 7.2.7, 7.2.8, 7.2.9, 7.2.10

## Audit and Safety Assumptions
- Audit-only behavior is the default; remediation is not implemented in this task.
- All Local Users and Groups tasks are read-only and use `changed_when: false`.
- No Internet dependencies are introduced.
- No risky account/group modification actions are executed.

## Missing Information Placeholders (Policy-Dependent)
- `MISSING_OT_BASELINE:approved_system_account_exceptions`
- `MISSING_OT_BASELINE:approved_duplicate_uid_exceptions`
- `MISSING_OT_BASELINE:approved_duplicate_gid_exceptions`
- `MISSING_OT_BASELINE:approved_duplicate_user_exceptions`
- `MISSING_OT_BASELINE:approved_duplicate_group_exceptions`
- `MISSING_OT_BASELINE:approved_interactive_users`

## OS Tested
- Local implementation validation host: macOS workstation used for repository work.
- Target ALT runtime testing: not executed in this workstation task.
- Runtime target facts are captured under `cis_local_users_groups_chapter.os_tested` during play execution.

## Commands Implemented (Audit Evidence Collection)
- `awk` checks on `/etc/passwd`, `/etc/shadow`, `/etc/group`
- `getent group <gid>` membership existence validation
- `find <home> -maxdepth 1 -type f -name '.*' -perm /022` for weak interactive-user dotfiles

## Evidence Records (Registered Outputs)
- `cis_7_2_1_non_shadowed`
- `cis_7_2_2_empty_shadow`
- `cis_7_2_3_missing_groups`
- `cis_7_2_4_shadow_group_members`
- `cis_7_2_5_duplicate_uids`
- `cis_7_2_6_duplicate_gids`
- `cis_7_2_7_duplicate_users`
- `cis_7_2_8_duplicate_group_names`
- `cis_7_2_9_interactive_users`
- `cis_7_2_10_weak_dotfiles`
- Aggregated chapter evidence: `cis_local_users_groups_chapter.evidence_records`

## Result Summary
- Per-control runtime status is aggregated into `cis_local_users_groups_chapter.result_summary`.
- Policy-dependent controls use `manual_review_required` where approved exceptions/baselines are missing.

ENGINEER APPROVAL REQUIRED BEFORE FINAL COMPLETION.
