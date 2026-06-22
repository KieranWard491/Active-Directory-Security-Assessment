# Active Directory Security Assessment

A penetration testing assessment conducted against a Windows Active Directory environment to identify weaknesses in authentication, access control, credential management, and delegated permissions.

The assessment involved network reconnaissance, SMB and LDAP enumeration, credential discovery, AS-REP Roasting, Kerberoasting, BloodHound analysis, privilege escalation through delegated permissions, and DCSync abuse, ultimately resulting in full domain compromise.

## Executive Summary

A security assessment was conducted against the Hawkins Active Directory environment to identify weaknesses in authentication, credential management, access controls, and privilege delegation.

Multiple vulnerabilities were identified, including exposed credentials, weak password practices, an AS-REP roastable account, excessive delegated permissions, and inappropriate DCSync privileges. These weaknesses enabled progression from a standard domain user to full domain compromise.

Recommendations have been provided to address the identified issues and reduce the likelihood of future compromise.

## Objectives

- Enumerate hosts and services within the environment
- Identify exposed credentials and authentication weaknesses
- Assess Active Directory security posture
- Discover privilege escalation paths
- Demonstrate the impact of identified vulnerabilities
- Obtain administrative access through legitimate attack paths
- Provide remediation recommendations

## Environment

### Target Environment

- Windows Active Directory Domain
- Domain Controller
- SMB Services
- LDAP Services
- Kerberos Authentication
- Multiple Domain User Accounts
- Network Shares

## Tools Used

### Reconnaissance & Enumeration

- Nmap
- SMBClient
- Enum4Linux
- LDAPSearch
- CrackMapExec

### Active Directory Analysis

- BloodHound
- SharpHound
- Neo4j

### Credential Attacks

- Impacket
- GetNPUsers
- GetUserSPNs
- John the Ripper

### Post-Exploitation

- Evil-WinRM
- SecretsDump
- PowerShell

## Attack Path

```text
Reconnaissance
      ↓
SMB Enumeration
      ↓
Credential Discovery
      ↓
AS-REP Roasting
      ↓
Kerberoasting
      ↓
BloodHound Analysis
      ↓
Group Membership Abuse
      ↓
DCSync
      ↓
Domain Compromise
```

## Assessment Methodology

### 1. Reconnaissance

Initial network reconnaissance was performed to identify active hosts, open ports, and exposed services within the environment.

### 2. SMB Enumeration

SMB shares were enumerated to identify accessible resources, sensitive information, and potential attack vectors.

### 3. Active Directory Enumeration

LDAP and Active Directory enumeration were conducted to gather information regarding users, groups, permissions, and domain configuration.

### 4. Credential Discovery

Multiple credential exposure issues were identified through accessible files, Active Directory attributes, and weak password practices.

### 5. AS-REP Roasting

Accounts configured without Kerberos pre-authentication were identified and targeted for offline password cracking.

### 6. Kerberoasting

Service accounts with registered SPNs were enumerated and Kerberos service tickets were extracted for offline password cracking.

### 7. Privilege Escalation

BloodHound analysis identified delegated permissions that could be abused to escalate privileges within the domain.

### 8. Domain Compromise

DCSync privileges were abused to retrieve domain credential material and achieve full domain compromise.

## Key Findings

### Exposed Credentials

Multiple user credentials were discovered through insecure storage practices and accessible files.

### Weak Password Practices

Default and weak passwords were identified, increasing the likelihood of successful credential attacks.

### AS-REP Roastable Accounts

Accounts configured without Kerberos pre-authentication were vulnerable to offline password attacks.

### Kerberoastable Service Accounts

Service accounts with weak passwords were susceptible to Kerberoasting attacks.

### Excessive Delegated Permissions

BloodHound analysis revealed privilege escalation paths through delegated group permissions.

### Inappropriate DCSync Privileges

Non-administrative accounts possessed permissions capable of performing DCSync operations.

## Recommendations

### Strengthen Password Policies

- Enforce complex password requirements
- Prohibit default passwords
- Implement regular password rotation
- Encourage unique passwords for service accounts

### Secure Service Accounts

- Use long, randomly generated passwords
- Implement Group Managed Service Accounts (gMSAs)
- Review and restrict SPN assignments

### Enable Kerberos Pre-Authentication

- Ensure all accounts require Kerberos pre-authentication
- Regularly audit authentication settings

### Restrict Active Directory Permissions

- Review delegated permissions
- Apply the principle of least privilege
- Monitor privileged group memberships

### Review DCSync Permissions

- Restrict replication permissions to authorised administrative accounts
- Regularly audit replication rights

### Secure Sensitive Information

- Remove credentials from files and account descriptions
- Restrict access to sensitive SMB shares
- Conduct periodic access reviews

## Skills Demonstrated

- Active Directory Enumeration
- SMB Enumeration
- LDAP Enumeration
- BloodHound Analysis
- AS-REP Roasting
- Kerberoasting
- Privilege Escalation
- Group Membership Abuse
- DCSync
- Windows Security Assessment
- Penetration Testing Methodology
- Security Reporting

## Repository Structure

```text
active-directory-security-assessment/
│
├── README.md
├── Active_Directory_Security_Assessment.pdf
├── screenshots/
│   ├── nmap_scan.png
│   ├── bloodhound_path.png
│   ├── kerberoast.png
│   └── dcsync.png
│
└── findings/
    └── recommendations.md
```

## Author

**Kieran Ward**

Computer Science Student | Cybersecurity & AI Enthusiast

GitHub: https://github.com/KieranWard491
