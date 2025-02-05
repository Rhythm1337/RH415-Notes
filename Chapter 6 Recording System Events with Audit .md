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
done!

# Topic 3 Inspecting Audit Logs 

## Interpreting Audit Messages

```
type=SYSCALL msg=audit(1371716130.596:28708): arch=c000003e syscall=2 success=yes exit=4
a0=261b130 a1=90800 a2=e a3=19 items=1 ppid=2548 pid=26131 auid=1000
uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=pts0 ses=1 comm="aureport" exe="/sbin/aureport"
subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 key="audit-access"
type=CWD msg=audit(1371716130.596:28708):  cwd="/root"
type=PATH msg=audit(1371716130.596:28708): item=0 name="/var/log/audit" inode=17998 dev=fd:01 mode=040750 ouid=0
ogid=0 rdev=00:00 obj=system_u:object_r:auditd_log_t:s0
```

**type=SYSCALL** 

It is a record/message type.

**msg=audit(1371716130.596:28708)**

This gives the time stamp and the event ID. 1371716130.596 is the time stamp 28708 is the Audit event number.

**syscall=2**

It is a type of the first record is SYSCALL, which shows information about a system call made to the kernel.

**auid=1000**

This records the Audit UID of the user that triggered this event.

**audit-access**

This is a identifier that you can use when searching for events

## Searching for Events

**By Time Start**

```
ausearch -ts recent -i 
ausearch -ts recent -i ./raw_audit.log
```

**By Process ID**

```
ausearch -p 1337 --raw
```

**By Event ID**

```
ausearch -a 99
```

**By Message Type**

```
ausearch -m AVC
ausearch -m LOGINS
```

AVC = SELinux

**By File Name**

```
ausearch -f /etc/shadow
```

**By Date**

```
--start [start-date] [start-time]
```

## Interpreting Audit Log Entries

```
ausearch -a 8888 -i
```

## Reporting on Audit Messages

```
aureport
ausearch -f /etc/shadow | aureport
```

## Tracing a Program

```
autrace /bin/bash
ausearch --raw -p 26472 | aureport --file -i
```

# Topic 4 Writing Custom Audit Rules
## Customizing Audit Rules
You can create custom Auditing Rules, Monitoring System call usage and file access, Auditing rules for compliance with industry standards and get a better understanding on how users and processes are using your system.

## Adding Rules
You can use auditctl command to add rules from the command line. By default if you add a audit rule, it will be added at the bottom of the current list but if you want to add the rule at the start of the list, that is possible too.

**The Audit System uses 3 types of rules**
- File System rules to monitor access to files and directories
- System Call rules to monitor the execution of system calls by processes
- Control rules configure the audit system itself

## Setting File System Watch Rules

```
auditctl -w file -p permession -k key
auditctl -w /etc/passwd -p wa -k user-edit
```

-w is name of file or directory to watch (r for read, w for write, x for execute, a for attribute changes)
-p is permission type
-k is a key set so you can search in auditctl

## Setting System Call Rules

```
auditctl -a <list>,<action> \
    [-F <filter-expression>]... \
    [-C <compare-expression>]... \
    [-S <system-call>]...
```

**Example Rules**

```
auditctl -a exit,always -F arch=b32 -F auid>=1000 -S rename \
    -S renameat -F subj_type!=mysqld_t -k rename
```

```
auditctl -a exclude,never -F auid=example \
    -F msgtype=USER_LOGIN -F success=0
```

## Setting Control Rules

Removes all Rules:

```
auditctl -D
```

Removes File System Rule that monitors /bin/ directory

```
auditctl -W /bin/
```

Setting Current System Rules to be immutable

```

```
