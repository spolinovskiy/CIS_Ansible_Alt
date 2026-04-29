# SSHD Chapter Report (ALT-1005)

## Scope
- Project: ALT Linux CIS Ansible for OT
- PRD task: ALT-1005
- Sheet/chapter: SSHD
- Control rows implemented: 5.1.1, 5.1.2, 5.1.3, 5.1.4, 5.1.5, 5.1.6, 5.1.7, 5.1.8, 5.1.9, 5.1.10, 5.1.11, 5.1.12, 5.1.13, 5.1.14, 5.1.15, 5.1.16, 5.1.17, 5.1.18, 5.1.19, 5.1.20, 5.1.21, 5.1.22
- Group header rows implemented: none (intentionally excluded)

## Status Buckets
- implemented: 5.1.1, 5.1.2, 5.1.3, 5.1.4, 5.1.5, 5.1.6, 5.1.7, 5.1.8, 5.1.9, 5.1.10, 5.1.11, 5.1.12, 5.1.13, 5.1.14, 5.1.15, 5.1.16, 5.1.17, 5.1.18, 5.1.19, 5.1.20, 5.1.21, 5.1.22
- skipped: none
- manual: none
- blocked: runtime-derived from `cis_sshd_chapter.blocked_controls`
- high-risk: 5.1.1, 5.1.2, 5.1.3, 5.1.4, 5.1.5, 5.1.6, 5.1.7, 5.1.8, 5.1.9, 5.1.10, 5.1.11, 5.1.12, 5.1.13, 5.1.14, 5.1.15, 5.1.16, 5.1.17, 5.1.18, 5.1.19, 5.1.20, 5.1.21, 5.1.22

## Audit and Safety Assumptions
- Audit-only behavior is the default; remediation is not implemented in this task.
- All SSHD tasks are read-only and use `changed_when: false`.
- No Internet dependencies are introduced.
- No risky remediation actions are executed.
- No SSH service restart/reload is performed.

## Missing Information Placeholders (OT Baselines)
- `MISSING_OT_BASELINE:approved_sshd_access_subnets`
- `MISSING_OT_BASELINE:approved_sshd_access_users`
- `MISSING_OT_BASELINE:approved_sshd_access_groups`
- `MISSING_OT_BASELINE:approved_sshd_ciphers`
- `MISSING_OT_BASELINE:approved_sshd_macs`
- `MISSING_OT_BASELINE:approved_sshd_kex_algorithms`
- `MISSING_OT_BASELINE:approved_banner_text_source`
- `MISSING_OT_BASELINE:approved_idle_session_settings`
- `MISSING_OT_BASELINE:approved_max_settings`

## OS Tested
- Local implementation validation host: macOS workstation used for repository work.
- Target ALT runtime testing: not executed in this workstation task.
- Runtime target facts are captured under `cis_sshd_chapter.os_tested` during play execution.

## Commands Implemented (Audit Evidence Collection)
- `stat /etc/ssh/sshd_config`
- `find /etc/ssh/sshd_config.d -name '*.conf'`
- `grep -RPs SSHD directives in sshd_config and sshd_config.d`
- `stat -c '%n|%U|%G|%a' /etc/ssh/ssh_host_*_key`
- `stat -c '%n|%U|%G|%a' /etc/ssh/ssh_host_*_key.pub`

## Evidence Records (Registered Outputs)
- `cis_sshd_main_config_stat`
- `cis_sshd_config_dir_stat`
- `cis_sshd_config_dir_find`
- `cis_5_1_2_private_key_stats`
- `cis_5_1_3_public_key_stats`
- `cis_sshd_control_checks`
- Aggregated chapter evidence: `cis_sshd_chapter.evidence_records`

## Result Summary
- Per-control runtime status is aggregated into `cis_sshd_chapter.result_summary`.
- Chapter-level blocked controls are aggregated into `cis_sshd_chapter.blocked_controls`.

## Temporary/Default Baseline Notes
- Access/subnet/user/group policy baselines are placeholders until engineer-approved OT values are provided.
- Ciphers/MACs/Kex allowlists and banner text source are placeholders until approved values are provided.
- Idle/session/max settings are placeholders until approved values are provided.

ENGINEER APPROVAL REQUIRED BEFORE FINAL COMPLETION.
