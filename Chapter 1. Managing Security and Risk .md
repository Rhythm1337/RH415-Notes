# Chapter 1. Managing Security and Risk

# Topic 1 Managing Security and Risk
## What you will learn ?
Discuss fundamental concepts of security management for RHEL Servers and how to approach the security management process.

## Managing Security
- Run: Run on a trusted platform
- Design: Identify security requirement
- Adapt: Revise and update policies
- Manage: Automate systems for security and compliance

> Rest is info about how Red Hat deals with security threats and more in much detail. (Read Book :P)

# Topic 2 Managing RHEL Security with Red Hat Errata
## What you will learn ?
Discussing Red Hat's security processes and install Red hat errata

> In the first section, we discuss how Red Hat deals with security fixes on older versions of packages and how audit teams deal with older versions of packages. (Read Book lol)

## Using DNF to Manage Security Errata

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

# Topic 3 Guided Exercise: Managing RHEL Security with Red Hat Errata
done!

# Topic 4 Reviewing Recommended Security Practices

## What you will learn ?
Implementing best practices to improve system security

Create a Standard Operating Envoirnment (SOE) is recommended insted of manual install

## Potential Risks to Services
- Denial of Service Attacks (DoS) [Very uncommon]
- Distributed Denial of Service Attacks (DDoS) [Common]
- Script Vulnerability Attacks [Uncommon]

# Topic 5 Reviewing Recommended Security Practices
## Commands

```
systemctl list-unit-files

ss -tlw
ss -tlwn

sudo update-crypto-policies --show
sudo update-crypto-policies --check
sudo update-crypto-policies --set legacy

ssk-keygen
ssh-copy-id
```

# Topic 6 Guided Exercise: Implementing Recommended Security Practices 
done!

# Topic 7 End of chapter Lab
done!
