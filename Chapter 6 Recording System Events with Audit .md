# Chapter 6. Recording System Events with Audit
# Topic 1 Configuring Audit to Record System Events

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

**Remote Logging**

Set the **log_format** = ENRICHED parameter to resolve the UID, GID, system call number, architecture, and socket address information
Set the **name_format** = HOSTNAME parameter to include the machine's hostname in each message.

### Rsyslog Remote Logging

Configure the rsyslog /etc/rsyslog.conf, Open the 514/UDP firewall port for standard syslog logging.

### Audit Remote Logging

If sending messages to remote auditd daemon, then install audispd-plugins package on client. On the client, the 
/etc/audit/plugins.d/audisp-remote.conf 
active = yes 

/etc/audit/audisp-remote.conf file
remote_server IP/ hostname auditd server.
Update the port if your remote server is not listening on the default 60/TCP port.

# Topic 2 Guided Exercise: Configuring Audit to Record System Events 
