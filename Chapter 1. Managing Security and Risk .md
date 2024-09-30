# Chapter 1. Managing Security and Risk
# Topic 1 Managing Security and Risk

**Managing Security**
- Run: Run on a trusted platform
- Design: Identify security requirement
- Adapt: Revise and update policies
- Manage: Automate systems for security and compliance

**Topic 2 Managing RHEL Security with Red Hat Errata**
  
**Using DNF to Manage Security Errata**

```
dnf updateinfo 
dnf updateinfo list updates security
dnf updateinfo list security --installed
dnf updateinfo list security --installed |  grep -i PACKAGE_NAME

dnf updateinfo list --cve CVE-2022-48383
dnf updateinfo list --cve CVE-2022-48383 --installed
dnf updateinfo info --cve CVE-2022-48383

dnf update --advisory=RSA-2023:3722
dnf update --security
```
