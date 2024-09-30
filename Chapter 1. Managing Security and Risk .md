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

# Topic 3 Guided Exercise: Managing RHEL Security with Red Hat Errata
done!

# Topic 4 Reviewing Recommended Security Practices
Create a Standard Operating Envoirnment (SOE) is recommended insted of manual install

**Potential Risks to Services**
- Denial of Service Attacks (DoS) [Very uncommon]
- Distributed Denial of Service Attacks (DDoS) [Common]
- Script Vulnerability Attacks [Uncommon]

**Commands**

```
systemctl list-unit-files

ss -tlw
ss -tlwn

update-crypto-policies --show
update-crypto-policies --check

```


