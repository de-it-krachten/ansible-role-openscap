[![CI](https://github.com/de-it-krachten/ansible-role-openscap/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-openscap/actions?query=workflow%3ACI)


# ansible-role-openscap

Installs & executes OpenSCAP for creating OVAL reports 



## Dependencies

#### Roles
- deitkrachten.cron

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Temporary directory to use
openscap_tmp_dir: /tmp

# Central location to store all servers reports
openscap_central_report_path: /var/log/openscap/central

# Log directory for holding reports etc
openscap_log_dir: /var/log/openscap

# Should report be created immediately
openscap_immediate: false

# Should daily report script be installed
openscap_schedule: false

# Command to schedule
openscap_schedule_command: "/usr/local/bin/openscap-oval-report.sh"

# Days & times for scheduling
openscap_schedule_times:
  weekday: '*'
  minute: '05'
  hour: '00'
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

### defaults/OracleLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://linux.oracle.com/security/oval/com.oracle.elsa-ol{{ ansible_distribution_major_version }}.xml.bz2
</pre></code>

### defaults/Ubuntu.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security-metadata.canonical.com/oval/com.ubuntu.{{ ansible_distribution_release }}.usn.oval.xml.bz2
</pre></code>

### defaults/RedHat.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.redhat.com/security/data/oval/com.redhat.rhsa-RHEL{{ ansible_distribution_major_version }}.xml.bz2
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

### defaults/Debian.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.debian.org/security/oval/oval-definitions-{{ ansible_distribution_release }}.xml
</pre></code>

### defaults/AlmaLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security.almalinux.org/oval/org.almalinux.alsa-{{ ansible_distribution_major_version }}.xml.bz2
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'openscap'
  hosts: all
  become: "yes"
  vars:
    openscap_gpg_recipient: foo@example.com
    openscap_gpg_key: "{{ lookup('file', 'files/foo.pub') }}"
  tasks:
    - name: Include role 'openscap'
      ansible.builtin.include_role:
        name: openscap
</pre></code>
