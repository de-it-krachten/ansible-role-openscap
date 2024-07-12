[![CI](https://github.com/de-it-krachten/ansible-role-openscap.dev-tmp/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-openscap.dev-tmp/actions?query=workflow%3ACI)


# ansible-role-openscap

Installs & executes OpenSCAP for creating OVAL reports 



## Dependencies

#### Roles
- deitkrachten.cron

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8<sup>1</sup>
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
openscap_oval: true
openscap_ssg: false

# Temporary directory to use
openscap_tmp_dir: /tmp

# Central location to store all servers reports
openscap_central_report_path: /var/log/openscap_central

# Location where a summary of the results will be written to
# This can be used to create an HTML report of all hosts
openscap_central_report_oval: "{{ openscap_central_report_path }}/index-oval.yml"

# download OVAL files centrally and distribute to nodes
openscap_central_download: false

# Collect reports to central location
openscap_central_collection: false

# File pattern of file to retrieve
# openscap_log_pattern: "*.bz2"
# openscap_log_pattern: "*.html,*.xml"
openscap_log_pattern: "*.html"

# Log directory for holding reports etc
openscap_log_dir: /var/log/openscap

# Should report be created immediately
openscap_oval_immediate: false

# Should daily report script be installed
openscap_oval_schedule: false

# Command to schedule
openscap_schedule_command: "/usr/local/bin/openscap-oval-report.sh"

# Use that should execute the commands
openscap_execution_user: root

# Days & times for scheduling
openscap_schedule_times:
  weekday: '*'
  minute: '05'
  hour: '00'

# OVAL report table
openscap_oval_table_name: OVAL
openscap_oval_table_headers:
  - host
  - os
  - version
  - date
  - time
  - vulnerabilities

# -------------------------------------------------
# scap-security-guide / ssg
# -------------------------------------------------

# Lookup table for ansible distribution and how they are named in SSG
openscap_ssg_distros:
  Ubuntu: "ubuntu{{ ansible_distribution_version | regex_replace('\\.') }}"
  CentOS: "centos{{ ansible_distribution_major_version }}"
  Debian: "debian{{ ansible_distribution_major_version }}"
  RedHat: "rhel{{ ansible_distribution_major_version }}"
  AlmaLinux: "rhel{{ ansible_distribution_major_version }}"
  Rocky: "rhel{{ ansible_distribution_major_version }}"
  OracleLinux: "ol{{ ansible_distribution_major_version }}"

# Perform audit
openscap_ssg_audit: false

# Perform hardening
openscap_ssg_hardening: false

# SSG file on Github
openscap_ssg_file: "scap-security-guide-{{ openscap_ssg_version | regex_replace('^v') }}.zip"

# Github CLI - API
openscap_ssg_api: https://api.github.com/repos/ComplianceAsCode/content

# Github CLI - repo
openscap_ssg_repo: https://github.com/ComplianceAsCode/content

# Version of the CLI to install
openscap_ssg_version: latest

# ssg location
openscap_ssg_root_path: /opt
openscap_ssg_path: "{{ openscap_ssg_root_path }}/scap-security-guide-{{ openscap_ssg_version | regex_replace('^v') }}"

openscap_report_path: /data/openscap

# List of action to include/exclude
openscap_ssg_tailoring:
  ubuntu2204:
    audit:
      select:
        # UFW
        - package_ufw_installed
        # chrony
        - package_chrony_installed
        # nftables
        # - package_nftables_removed
        - service_nftables_disabled
      unselect:
        ## AIDE
        # - aide_build_database
        # nftables
        - set_nftables_table
        - set_nftables_loopback_traffic
        - set_nftables_base_chain
        - nftables_rules_permanent
        - nftables_ensure_default_deny_policy
        - package_nftables_installed
        - service_nftables_enabled
        - group_network-nftables
        # ufw
        - package_ufw_removed
        # timesyncd
        - package_timesyncd_installed
        - service_ntp_enabled
        - service_timesyncd_enabled
        - ntpd_run_as_ntp_user
        - ntpd_configure_restrictions
        # rsync
        - package_rsync_removed
        # sshd
        - sshd_limit_user_access
    hardening:
      unselect:
        # umask
        - accounts_umask_etc_profile
        - accounts_umask_etc_bashrc
        - accounts_umask_etc_login_defs

# OVAL report table
openscap_ssg_table_name: Hardening
openscap_ssg_table_headers:
  - host
  - os
  - version
  - date
  - time

# Location where a summary of the results will be written to
# This can be used to create an HTML report of all hosts
openscap_central_report_ssg: "{{ openscap_central_report_path }}/index-ssg.yml"
</pre></code>

### defaults/AlmaLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security.almalinux.org/oval/org.almalinux.alsa-{{ ansible_distribution_major_version }}.xml.bz2
</pre></code>

### defaults/Debian-12.yml
<pre><code>
# list of required packages
openscap_packages:
  - openscap-scanner
  - openscap-utils
  - bzip2
  - gpg
  - wget
</pre></code>

### defaults/Debian.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.debian.org/security/oval/oval-definitions-{{ ansible_distribution_release }}.xml.bz2
</pre></code>

### defaults/family-Debian.yml
<pre><code>
# list of required packages
openscap_packages:
  # - openscap-daemon
  - libopenscap8
  - bzip2
  - gpg
  - wget
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
# list of required packages
openscap_packages:
  - openscap
  - openscap-scanner
  - bzip2
  - gpg
  - wget
</pre></code>

### defaults/OracleLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://linux.oracle.com/security/oval/com.oracle.elsa-ol{{ ansible_distribution_major_version }}.xml.bz2
</pre></code>

### defaults/RedHat.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.redhat.com/security/data/oval/v2/RHEL{{ ansible_distribution_major_version }}/rhel-{{ ansible_distribution_major_version }}.oval.xml.bz2
</pre></code>

### defaults/Rocky.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://dl.rockylinux.org/pub/oval/org.rockylinux.rlsa-{{ ansible_distribution_major_version }}.xml.bz2
</pre></code>

### defaults/Sles.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://support.novell.com/security/oval/suse.linux.enterprise.server.{{ ansible_distribution_major_version }}.xml
</pre></code>

### defaults/Ubuntu-24.yml
<pre><code>
# list of required packages
openscap_packages:
  # - openscap-daemon
  - openscap-common
  - openscap-utils
  - bzip2
  - gpg
  - wget
</pre></code>

### defaults/Ubuntu.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security-metadata.canonical.com/oval/com.ubuntu.{{ ansible_distribution_release }}.usn.oval.xml.bz2
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'openscap'
  hosts: all
  become: 'False'
  vars:
    openscap_central_download: true
    openscap_central_collection: true
    openscap_central_path: /var/log/openscap_central
    openscap_central_mode: '0644'
    openscap_oval: true
    openscap_oval_immediate: true
    openscap_ssg: true
    openscap_ssg_audit: true
    openscap_schedule_command: /usr/local/bin/openscap-oval-report.sh -D
    openscap_gpg_recipient: foo@example.com
    openscap_gpg_key: '{{ lookup(''file'', ''files/foo.pub'') }}'
  tasks:
    - name: Include role 'openscap.dev-tmp'
      ansible.builtin.include_role:
        name: openscap.dev-tmp
</pre></code>
