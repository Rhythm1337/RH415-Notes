# Chapter 6. Recording System Events with Audit
#  Configuring Audit to Record System Events

**Linux Audit System**

- date, time, type and outcome
- sensitivity lables
- which user is causing the alert
- modifications to the audit config and attempts to change the audit log file
- use of authentication methods like ssh, kerbos, etc
- changes to any trusted databases such as /etc/passwd file
- attempts to import and export information

**Configuring the Audit Daemon**

Primary file for configuring auditd daemon
auditd daemon uses this file to load audit rules
This directory contains manually configured audit rules

```
/etc/audit/auditd.conf
/etc/audit/audit.rules
/etc/audit/rules.d/
```

