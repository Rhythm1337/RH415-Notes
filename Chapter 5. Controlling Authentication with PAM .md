# Chapter 5. Controlling Authentication with PAM
# Topic 1  Selecting the PAM Configuration

**What is PAM ?**
Pluggable Authentication Modules

 **Authentication**

- LDAP Server with TLS
- LDAP Server for account info with kerberos for password peices
- 2FA
- UBI Key
- Fingerprint Reader
- Etc

**PAM**

```
ls /usr/lib64/security
ls /etc/security/

ls /etc/pam.d/
ls /etc/authselect/
authselect list
authselect list-features minimal
authselect select minimal with-pwhistory
```

**Reading PAM Configuration Files**

```
type  control  module  [module arguments]

auth     required pam_env.so
account     [default=bad success=ok user_unknown=ignore] pam_sss.so
```
