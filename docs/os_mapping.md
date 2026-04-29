# ALT Linux OS Mapping

Task `ALT-0005` defines OS/version mapping files for the independent ALT Linux CIS Ansible project. These files do not implement CIS controls and do not expand the scope beyond `linux_cis.xlsx`.

## Evidence Level

No ALT lab host facts were available during this task. Common ALT version identifiers such as p10/10.x and p11/11.x are recorded only as `candidate_untested`. No version is marked tested.

ALT package management is mapped as `apt_rpm` with RPM query fallback, but this is `candidate_unverified`. Package installation and removal must remain blocked unless all required gates are true: `remediation_enabled`, `package_install_allowed`, and `local_repository_defined`. Removal also requires `destructive_changes_allowed` and approval.

## Fact Handling

Future playbooks must use these Ansible facts for OS/version decisions:

- `ansible_distribution`
- `ansible_distribution_version`
- `ansible_distribution_major_version`
- `ansible_os_family`
- `ansible_kernel`

Unsupported or unknown ALT versions must fail safely, or run audit-only only when explicitly allowed by `alt_allow_unknown_version_audit_only` and mark version-dependent controls as `manual_review_required`.

## Mapping Files

- `data/os_map/supported_versions.yml` records ALT distribution matching, candidate untested versions, fact keys, unknown-version policy, and execution guards.
- `data/os_map/packages.yml` maps package manager behavior and candidate package names for sudo, PAM, SSH, cron/at, time sync, logging/audit, bootloader, filesystem, network, and service/client areas.
- `data/os_map/services.yml` maps candidate systemd unit names for sshd, cron/at, chrony, systemd-timesyncd, journald, rsyslog, auditd, and service inventory candidates.
- `data/os_map/paths.yml` maps candidate ALT paths for sudo, PAM, SSH, cron/at, time sync, logging, auditd, bootloader, filesystem, sysctl, banners, packages, and account files.
- `data/os_map/commands.yml` maps read-only audit commands and guarded remediation/package commands.
- `data/os_map/features.yml` maps feature availability and unknowns for apt-rpm/RPM, systemd, MAC frameworks, bootloader, PAM layout, logging, time sync, firewall, filesystem, and OT safety.

## Caveats

Debian/Ubuntu reference paths such as `/etc/pam.d/common-*` are retained only as `debian_reference_only_not_alt_verified` because source scripts and benchmark PDFs use those patterns. ALT-specific PAM package splits, service unit names, repository layout, bootloader path, and systemd-timesyncd availability must be verified against real ALT hosts or an approved local repository before remediation.

No Internet repository URLs, package sources, credentials, or production values are defined.
