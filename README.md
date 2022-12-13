[![CI](https://github.com/de-it-krachten/ansible-role-openscap/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-openscap/actions?query=workflow%3ACI)


# ansible-role-openscap

Installs & executes OpenSCAP for rcreating OVAL reports 



## Dependencies

#### Roles
- cron

#### Collections
- community.general
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
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
# Temporrary directory to use
openscap_tmp_dir: /tmp

# Should report be created immediately
openscap_execution: true

# Should daily report script be installed
openscap_schedule: false
</pre></code>

### defaults/Debian.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.debian.org/security/oval/oval-definitions-{{ ansible_distribution_release }}.xml

# list of required packages
openscap_packages:
  - openscap-daemon
  - bzip2
  - gpg
  - curl
  - sshpass
</pre></code>

### defaults/AlmaLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security.almalinux.org/oval/org.almalinux.alsa-{{ ansible_distribution_major_version }}.xml.bz2

# list of required packages
openscap_packages:
  - openscap
  - openscap-scanner
  - bzip2
  - gpg
  - curl
  - sshpass
</pre></code>

### defaults/Ubuntu.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://security-metadata.canonical.com/oval/com.ubuntu.{{ ansible_distribution_release }}.usn.oval.xml.bz2

# list of required packages
openscap_packages:
  - openscap-daemon
  - bzip2
  - gpg
  - curl
  - sshpass
</pre></code>

### defaults/RedHat.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://www.redhat.com/security/data/oval/com.redhat.rhsa-RHEL{{ ansible_distribution_major_version }}.xml.bz2

# list of required packages
openscap_packages:
  - openscap
  - openscap-scanner
  - bzip2
  - gpg
  - curl
  - sshpass
</pre></code>

### defaults/OracleLinux.yml
<pre><code>
# OVAL download url
openscap_url: >-
  https://linux.oracle.com/security/oval/com.oracle.elsa-ol{{ ansible_distribution_major_version }}.xml.bz2

# list of required packages
openscap_packages:
  - openscap
  - openscap-scanner
  - bzip2
  - gpg
  - curl
  - sshpass
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'openscap'
  hosts: all
  become: "yes"
  tasks:
    - name: Include role 'openscap'
      ansible.builtin.include_role:
        name: openscap
</pre></code>
