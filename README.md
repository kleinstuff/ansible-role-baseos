[![Build Status](https://travis-ci.org/kleinstuff/ansible-role-baseos.png)](https://travis-ci.org/kleinstuff/ansible-role-baseos)

ansible-role-baseos
=========

Install and configure some baseos settings
* User creation
* SELinux enforcing
* Timezone
* Setup SUDO to allow users from group wheel to use it without password
* Setup sshd_config

This role should not have:
* Security/Monitoring agents (should have their own role)
* Application configurations (should have their own role)

Requirements
------------

N/A

Role Variables
--------------

All variables need to have "role_baseos_varname" format

| var name |type | default value |
|----------|---------------|---------------|
|          |               |               |
|role_baseos__selinuxstatus|string|"enforcing"|
|role_baseos__users|dict|(notset)"name: "user1", state: "present", groups: "ExtraGroupsForUser1", authorized_key: "ssh-rsa bigrsakey", jail: "no", AllowPass: "no", AllowTunnel: "yes"|
|role_baseos__sshports|list|"22"|
|role_baseos__timezone|string|"America/Sao_paulo"|
|role_baseos__hostname|string|not set|



Dependencies
------------

This role does not depend on any other role.

Example Playbook
----------------

```yaml
- hosts: all
  become: yes
  roles:
    - { role: ansible-role-baseos }
  vars:
    role_baseos_users:
      - {"name: "user1", state: "present", groups: "ExtraGroupsForUser1", authorized_key: "ssh-rsa bigrsakey", jail: "no", AllowPass: "no", AllowTunnel: "yes"}
```

License
-------

GPLv3

Author Information
------------------

If you want to suggest changes or request new features, please feel free to create a issue or send a pull request.

ToDo
------------------
 - Add UnitTests (Molecule FTW)
 - Test Against CentOS7 and CentOS8
 - Add Suport to (open)SUSE (and apparmor hardening instead of selinux in this case)
