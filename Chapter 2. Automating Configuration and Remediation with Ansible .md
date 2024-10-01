# Chapter 2. Automating Configuration and Remediation with Ansible 

**Installing Ansible**

```
subscription-manager repos --enable ansible-automation-platform-2.4-for-rhel-9-x86_64-rpms
dnf install ansible-navigator
ansible-navigator --version
podman login registry.redhat.io
ansible-navigator images
```

**Preparing Managed Hosts for Ansible Automation**
- On Linux and UNIX managed hosts, Python 3.8 or later must be installed for most modules to work.
- If SELinux is enabled on the managed hosts, then ensure that the python3-libselinux package is installed before using modules that are related to any copy, file, or template functions.
- Ansible must connect to the managed machine by using SSH. When Ansible connects as a regular user, it must be able to use sudo to gain superuser access.

**In /etc/sudoers.d/ansible-testuser**

```
ansible-testuser  ALL=(ALL) ALL
or
ansible-testuser  ALL=(ALL) NOPASSWD:ALL
```

**Managing a Host Inventory**

```
[minecraft]
servera
serverb

[rust]
serverc
serverc

[games:children]
minecraft
rust
```

**Ansible Custom .cfg**

```
[defaults]
inventory = ./inventory
remote_user = user
ask_pass = false

[privilege_escalation]
become = true
become_method = sudo
become_user = root
become_ask_pass = false
```

**Commands (do -m stdout for everything displayed on the terminal)**

```
ansible-navigator config
ansible-navigator collections
ansible-navigator doc ansible.posix.firewalld

ansible-navigator -m stdout playbook.yml
ansible-navigator -m stdout playbook.yml --syntax-check
ansible-navigator -m stdout playbook.yml --check


```

**Example Play**

```
---
- name: Configure important user consistently
  hosts: servera
  tasks:
    - name: clashroyale exists with UID 4000
      ansible.builtin.user:
        name: clashroyale
        uid: 9999
        state: present
```

# Topic 2 Guided Exercise: Configuring Ansible for Security Automation
done!

# Topic 3 Managing Playbooks with Automation Controller
> basically ansible but with gui

# Topic 4 Guided Exercise: Managing Playbooks with Automation Controller 
done!

# Topic 5 End of chapter Lab
done!
