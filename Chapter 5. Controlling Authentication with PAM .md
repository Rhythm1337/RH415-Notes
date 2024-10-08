# Chapter 5. Controlling Authentication with PAM
# Topic 1 Selecting the PAM Configuration

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

# Topic 2 Guided Exercise: Selecting the PAM Configuration
done!

**Topic 3 Configuring Password Quality Requirements**

```
grep ^password /etc/pam.d/sshd
grep ^password /etc/pam.d/login (locally)

grep ^password /etc/pam.d/systemauth 
grep ^password /etc/pam.d/passwd
```

**Configuring the PAM Password Quality Module**

```
cat /etc/security/pwquality.conf.d/
```

**Configuring a Password Policy**

In ```vim /etc/security/pwquality.conf.d/```

- atleast 8 characters
- atleast 1 uppercase letter
- atleast 2 digits
- atleast 1 special character

```
minlen=8
lcredit=1
ucredit=-1
dcredit=-2
ocredit=-1
```

# Topic 4 Guided Exercise: Configuring Password Quality Requirements
done!

# Topic 5 Limiting Access after Failed Logins

**pam_faillock Module**

```
authselect select minimal with-fallback --force
cat /etc/security/faillock.conf
```

**Locked Accounts**

```
faillock
faillock --user minecraft
faillock --user minecraft --reset
```

# Topic 6 Guided Exercise: Limiting Access after Failed Logins
done!

# Topic 7 End of chapter Lab
done!
