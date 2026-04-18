## Chapter 10: Security, Compliance, and Governance

---

### 📚 What You'll Learn in This Chapter

By the end of this chapter, you'll understand:

- ✓ Defense in Depth (7 layers of security)
- ✓ Azure Active Directory (Azure AD)
- ✓ RBAC (Role-Based Access Control)
- ✓ Azure Policy (enforce rules)
- ✓ Microsoft Defender for Cloud
- ✓ Azure Key Vault
- ✓ Compliance and certifications

**Time needed:** 25-30 minutes  
**Difficulty:** Moderate 🟡

**Why this matters:** Security is tested heavily on AZ-900 and is critical for real-world Azure usage!

---

## Defense in Depth

### What is Defense in Depth?

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ DEFENSE IN DEPTH:                                               │
│ Multiple layers of security, like a medieval castle            │
│                                                                 │
│ If attacker breaches one layer, they face many more!           │
│                                                                 │
│ Think: Castle with moat → walls → guards → locked doors        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### The 7 Layers of Security

```
┌──────────────────────────────────────────────────────────────┐
│ DEFENSE IN DEPTH - 7 LAYERS                                  │
│                                                              │
│            ┌───────────────────────┐                         │
│            │  LAYER 7: DATA        │ ← What you protect     │
│            │  • Encryption         │                         │
│            │  • Access control     │                         │
│            └───────────────────────┘                         │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 6: APPLICATION   │                          │
│         │  • Secure coding        │                          │
│         │  • WAF                  │                          │
│         └─────────────────────────┘                          │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 5: COMPUTE       │                          │
│         │  • VM security          │                          │
│         │  • Endpoint protection  │                          │
│         └─────────────────────────┘                          │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 4: NETWORK       │                          │
│         │  • Segmentation         │                          │
│         │  • DDoS protection      │                          │
│         └─────────────────────────┘                          │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 3: PERIMETER     │                          │
│         │  • Firewall             │                          │
│         │  • VPN                  │                          │
│         └─────────────────────────┘                          │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 2: IDENTITY      │                          │
│         │  • Azure AD             │                          │
│         │  • MFA                  │                          │
│         └─────────────────────────┘                          │
│                      ▲                                       │
│         ┌────────────┴────────────┐                          │
│         │  LAYER 1: PHYSICAL      │                          │
│         │  • Datacenter security  │                          │
│         │  • Biometric access     │                          │
│         └─────────────────────────┘                          │
│                                                              │
│ Attacker must breach ALL layers to access data! 🛡️           │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### How Each Layer Protects You

```
LAYER 1 - PHYSICAL SECURITY:
┌──────────────────────────────────────────────────────────────┐
│ Microsoft's Responsibility                                   │
│                                                              │
│ • Biometric scanners (fingerprint/retina)                   │
│ • 24/7 armed security guards                                 │
│ • Restricted access zones                                   │
│ • Surveillance cameras                                      │
│ • Mantrap entrances                                         │
│                                                              │
│ Example Attack Stopped:                                      │
│ Hacker tries to physically enter datacenter                  │
│ → Blocked by security guards ✓                              │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 2 - IDENTITY & ACCESS:
┌──────────────────────────────────────────────────────────────┐
│ Your Responsibility                                          │
│                                                              │
│ • Multi-Factor Authentication (MFA)                          │
│ • Strong passwords                                           │
│ • Conditional Access policies                               │
│ • Least privilege access                                    │
│                                                              │
│ Example Attack Stopped:                                      │
│ Hacker steals password                                       │
│ → MFA required (don't have phone) ✓                         │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 3 - PERIMETER:
┌──────────────────────────────────────────────────────────────┐
│ • Firewall rules                                            │
│ • DDoS protection                                           │
│ • VPN for remote access                                     │
│                                                              │
│ Example Attack Stopped:                                      │
│ DDoS attack (1 million requests/second)                      │
│ → Azure DDoS Protection absorbs attack ✓                    │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 4 - NETWORK:
┌──────────────────────────────────────────────────────────────┐
│ • Network Security Groups (NSGs)                             │
│ • Network segmentation                                      │
│ • Private endpoints                                         │
│                                                              │
│ Example Attack Stopped:                                      │
│ Hacker compromises web server                                │
│ → Can't reach database (different subnet, NSG blocks) ✓     │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 5 - COMPUTE:
┌──────────────────────────────────────────────────────────────┐
│ • Antivirus/Antimalware                                     │
│ • VM updates and patches                                    │
│ • Just-in-time VM access                                    │
│                                                              │
│ Example Attack Stopped:                                      │
│ Malware uploaded to VM                                       │
│ → Antimalware detects and quarantines ✓                    │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 6 - APPLICATION:
┌──────────────────────────────────────────────────────────────┐
│ • Secure coding practices                                   │
│ • SQL injection protection                                  │
│ • Web Application Firewall (WAF)                            │
│                                                              │
│ Example Attack Stopped:                                      │
│ SQL injection attack on web form                             │
│ → WAF detects malicious SQL and blocks ✓                    │
│                                                              │
└──────────────────────────────────────────────────────────────┘

LAYER 7 - DATA:
┌──────────────────────────────────────────────────────────────┐
│ • Encryption at rest                                        │
│ • Encryption in transit                                     │
│ • Data classification                                       │
│ • Access controls                                           │
│                                                              │
│ Example Attack Stopped:                                      │
│ Hacker steals database backup                                │
│ → Data encrypted, useless without key ✓                     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Azure Active Directory (Azure AD)

### What is Azure AD?

**Identity and access management service for the cloud!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ AZURE AD:                                                       │
│ Who are you? Can you access this resource?                     │
│                                                                 │
│ Think: Security guard checking IDs                             │
│                                                                 │
│ Manages: Users, groups, authentication, authorization          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### Key Azure AD Features

```
1. SINGLE SIGN-ON (SSO)
┌──────────────────────────────────────────────────────────────┐
│ WITHOUT SSO (Annoying):                                      │
│                                                              │
│ Login to Office 365 → Enter email + password                 │
│ Login to Azure Portal → Enter email + password again         │
│ Login to CRM system → Enter email + password again           │
│ Login to HR system → Enter email + password again            │
│                                                              │
│ 4 different logins! 😫                                       │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ WITH SSO (Easy):                                             │
│                                                              │
│ Login ONCE to Azure AD → Logged in everywhere! ✓             │
│                                                              │
│ Access Office 365 → Already logged in ✓                      │
│ Access Azure Portal → Already logged in ✓                    │
│ Access CRM → Already logged in ✓                             │
│ Access HR → Already logged in ✓                              │
│                                                              │
│ One login for everything! 🎉                                 │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

```
2. MULTI-FACTOR AUTHENTICATION (MFA)
┌──────────────────────────────────────────────────────────────┐
│ Two-step verification for security                           │
│                                                              │
│ SOMETHING YOU KNOW + SOMETHING YOU HAVE                       │
│                                                              │
│ Login Process:                                               │
│                                                              │
│ Step 1: Enter password ────────────► "password123" ✓         │
│         (Something you know)                                  │
│                                                              │
│ Step 2: Enter code from phone ────► "487291" ✓               │
│         (Something you have)                                  │
│                                                              │
│ Both correct? → Access granted! ✓                            │
│                                                              │
│ WHY IT'S SECURE:                                              │
│ Hacker steals your password?                                 │
│ → Still can't login (don't have your phone!) ✓              │
│                                                              │
│ MFA METHODS:                                                  │
│ • Text message (SMS)                                        │
│ • Phone call                                                │
│ • Microsoft Authenticator app (best!)                       │
│ • Hardware token                                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

```
3. CONDITIONAL ACCESS
┌──────────────────────────────────────────────────────────────┐
│ Smart rules that adapt to context                            │
│                                                              │
│ EXAMPLE POLICY:                                               │
│                                                              │
│ "If user is:                                                 │
│  • In the office → No MFA needed                            │
│  • At home → MFA required                                    │
│  • In foreign country → Block access completely"             │
│                                                              │
│ SCENARIO 1:                                                   │
│ Sarah logs in from office                                    │
│ → Recognized office IP                                       │
│ → Password only (no MFA) ✓                                   │
│                                                              │
│ SCENARIO 2:                                                   │
│ Sarah logs in from home                                      │
│ → Unknown location                                           │
│ → Password + MFA required ✓                                  │
│                                                              │
│ SCENARIO 3:                                                   │
│ Hacker in Russia tries to login as Sarah                     │
│ → Foreign country detected                                   │
│ → Access blocked completely! ✓                               │
│ → Alert sent to admin                                        │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## RBAC (Role-Based Access Control)

### What is RBAC?

**Control WHO can do WHAT!**

```
┌──────────────────────────────────────────────────────────────┐
│ RBAC = Assigning permissions based on job roles              │
│                                                              │
│ FORMULA:                                                      │
│                                                              │
│ Security Principal + Role + Scope = Assignment                │
│     (WHO)           (WHAT)  (WHERE)                          │
│                                                              │
│ Example:                                                      │
│ John (WHO) + Reader (WHAT) + Production (WHERE)              │
│ = John can view Production resources                         │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Built-in Roles

```
┌──────────────────────────────────────────────────────────────┐
│ MAIN RBAC ROLES (Know these for exam!)                      │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ 1. OWNER                                                     │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Can do: EVERYTHING                                   │ │
│    │ • Create resources ✓                                 │ │
│    │ • Delete resources ✓                                 │ │
│    │ • Assign permissions to others ✓                     │ │
│    │                                                      │ │
│    │ Use for: Admins, subscription owners                 │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 2. CONTRIBUTOR                                               │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Can do: Create and manage resources                  │ │
│    │ • Create resources ✓                                 │ │
│    │ • Delete resources ✓                                 │ │
│    │ • Assign permissions ❌ (CANNOT!)                    │ │
│    │                                                      │ │
│    │ Use for: Developers, IT staff                        │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 3. READER                                                    │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Can do: View only (read-only)                        │ │
│    │ • View resources ✓                                   │ │
│    │ • Create resources ❌                                │ │
│    │ • Modify resources ❌                                │ │
│    │                                                      │ │
│    │ Use for: Auditors, read-only access                  │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 4. USER ACCESS ADMINISTRATOR                                 │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Can do: Manage user access                           │ │
│    │ • Assign roles ✓                                     │ │
│    │ • Manage resources ❌                                │ │
│    │                                                      │ │
│    │ Use for: Security admins                             │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### RBAC Scope Levels

```
SCOPE HIERARCHY (Top to Bottom):

┌──────────────────────────────────────────────────────────────┐
│                                                              │
│ 1. MANAGEMENT GROUP (Largest scope)                          │
│    ┌────────────────────────────────────────────────────┐   │
│    │ Permissions apply to ALL subscriptions under this  │   │
│    │ Example: CEO has Owner on Management Group         │   │
│    │ → Controls everything in company                   │   │
│    └────────────────────────────────────────────────────┘   │
│                    ↓ (Inherits down)                         │
│ 2. SUBSCRIPTION                                              │
│    ┌────────────────────────────────────────────────────┐   │
│    │ Permissions apply to all resource groups in sub    │   │
│    │ Example: IT Manager has Contributor on Sub         │   │
│    │ → Can manage all resources in subscription         │   │
│    └────────────────────────────────────────────────────┘   │
│                    ↓ (Inherits down)                         │
│ 3. RESOURCE GROUP                                            │
│    ┌────────────────────────────────────────────────────┐   │
│    │ Permissions apply to all resources in RG           │   │
│    │ Example: Developer has Contributor on "WebApp-RG"  │   │
│    │ → Can manage all resources in that RG              │   │
│    └────────────────────────────────────────────────────┘   │
│                    ↓ (Inherits down)                         │
│ 4. RESOURCE (Smallest scope)                                 │
│    ┌────────────────────────────────────────────────────┐   │
│    │ Permissions apply to single resource only          │   │
│    │ Example: Intern has Reader on specific VM          │   │
│    │ → Can only view that one VM                        │   │
│    └────────────────────────────────────────────────────┘   │
│                                                              │
│ INHERITANCE: Permissions flow DOWN the hierarchy             │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Real-World RBAC Example

```
COMPANY: Tech Startup

┌──────────────────────────────────────────────────────────────┐
│ SUBSCRIPTION: Production                                     │
│                                                              │
│ CEO (Sarah):                                                 │
│ • Role: Owner (Subscription level)                           │
│ • Can: Everything                                            │
│                                                              │
│ IT Manager (Mike):                                           │
│ • Role: Contributor (Subscription level)                     │
│ • Can: Create/manage resources, but not assign permissions   │
│                                                              │
│ Developer (John):                                            │
│ • Role: Contributor (Resource Group: "Dev-RG" only)          │
│ • Can: Manage resources in Dev-RG only                       │
│ • Cannot: Touch Production-RG                                │
│                                                              │
│ Intern (Alice):                                              │
│ • Role: Reader (Resource Group: "Dev-RG")                    │
│ • Can: View resources in Dev-RG                              │
│ • Cannot: Make any changes                                   │
│                                                              │
│ Auditor (Bob):                                               │
│ • Role: Reader (Subscription level)                          │
│ • Can: View everything                                       │
│ • Cannot: Make any changes anywhere                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Azure Policy

### What is Azure Policy?

**Enforce rules and standards automatically!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ AZURE POLICY:                                                   │
│ Automated rules that prevent non-compliant resources           │
│                                                                 │
│ RBAC says: WHO can do WHAT                                      │
│ Policy says: WHAT can be created                               │
│                                                                 │
│ Think: Company rules enforced by software                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### How Azure Policy Works

```
┌──────────────────────────────────────────────────────────────┐
│ POLICY IN ACTION                                             │
│                                                              │
│ EXAMPLE POLICY:                                               │
│ "All storage accounts must use encryption"                    │
│                                                              │
│ SCENARIO 1 - Compliant:                                       │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Developer tries to create storage account              │   │
│ │          ↓                                             │   │
│ │ Encryption: Enabled ✓                                  │   │
│ │          ↓                                             │   │
│ │ Policy checks: "Encryption enabled?" YES               │   │
│ │          ↓                                             │   │
│ │ Storage account created! ✓                             │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ SCENARIO 2 - Non-Compliant:                                  │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Developer tries to create storage account              │   │
│ │          ↓                                             │   │
│ │ Encryption: Disabled ❌                                │   │
│ │          ↓                                             │   │
│ │ Policy checks: "Encryption enabled?" NO                │   │
│ │          ↓                                             │   │
│ │ BLOCKED! ❌                                             │   │
│ │ Error: "Policy violation: Encryption required"         │   │
│ │          ↓                                             │   │
│ │ Developer must fix or request exception                │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Common Azure Policies

```
TOP 10 POLICIES (Examples):

┌──────────────────────────────────────────────────────────────┐
│ 1. "Allowed locations"                                       │
│    Only create resources in East US or West US               │
│    Prevents: Accidentally deploying to expensive regions     │
│                                                              │
│ 2. "Require tag on resources"                                │
│    Every resource must have "Owner" tag                      │
│    Prevents: Unknown resource ownership                      │
│                                                              │
│ 3. "Allowed virtual machine SKUs"                            │
│    Only use B-series and D-series VMs                        │
│    Prevents: Expensive VM sizes                              │
│                                                              │
│ 4. "Require encryption on storage accounts"                  │
│    All storage must be encrypted                             │
│    Prevents: Data breaches                                   │
│                                                              │
│ 5. "Require automatic backup"                                │
│    VMs must have backup enabled                              │
│    Prevents: Data loss                                       │
│                                                              │
│ 6. "Block public IP addresses"                               │
│    VMs cannot have public IPs                                │
│    Prevents: Direct internet exposure                        │
│                                                              │
│ 7. "Require HTTPS only"                                      │
│    Web apps must use HTTPS                                   │
│    Prevents: Unencrypted traffic                             │
│                                                              │
│ 8. "Allowed resource types"                                  │
│    Only VMs, Storage, and Networks allowed                   │
│    Prevents: Unauthorized services                           │
│                                                              │
│ 9. "Require anti-malware extension"                          │
│    All VMs must have antivirus                               │
│    Prevents: Malware infections                              │
│                                                              │
│ 10. "Require disaster recovery"                              │
│     Resources must replicate to paired region                │
│     Prevents: Single point of failure                        │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Microsoft Defender for Cloud

### What is Defender for Cloud?

**Security monitoring and recommendations for Azure!**

```
┌──────────────────────────────────────────────────────────────┐
│ DEFENDER FOR CLOUD FEATURES                                  │
│                                                              │
│ 1. SECURE SCORE                                              │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Your Security: 65/100 ⚠️                             │ │
│    │                                                      │ │
│    │ Recommendations:                                     │ │
│    │ • Enable MFA for admins (+15 points)                │ │
│    │ • Update VM operating systems (+10 points)          │ │
│    │ • Enable encryption on storage (+8 points)          │ │
│    │ • Configure firewall rules (+12 points)             │ │
│    │                                                      │ │
│    │ Fix all → Score becomes 100! ✓                      │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 2. THREAT PROTECTION                                         │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Monitors for attacks:                                │ │
│    │ • Brute force login attempts                         │ │
│    │ • Malware uploads                                    │ │
│    │ • Suspicious network traffic                         │ │
│    │ • Data exfiltration                                  │ │
│    │                                                      │ │
│    │ Alerts you immediately! 🚨                           │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 3. COMPLIANCE DASHBOARD                                      │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ GDPR Compliance: 78% ⚠️                              │ │
│    │ HIPAA Compliance: 92% ✓                              │ │
│    │ PCI-DSS Compliance: 85% ⚠️                           │ │
│    │                                                      │ │
│    │ Shows what you need to fix for compliance            │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Azure Key Vault

### What is Key Vault?

**Secure storage for secrets, keys, and certificates!**

```
┌──────────────────────────────────────────────────────────────┐
│ KEY VAULT - SECURE SECRET STORAGE                            │
│                                                              │
│ PROBLEM (Bad Practice):                                      │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Your application code:                                 │   │
│ │                                                        │   │
│ │ database_password = "MyPassword123"  ❌ VISIBLE!       │   │
│ │ api_key = "abc123xyz789"            ❌ IN CODE!        │   │
│ │                                                        │   │
│ │ Anyone with code access sees secrets!                  │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ SOLUTION (Key Vault):                                        │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Your application code:                                 │   │
│ │                                                        │   │
│ │ password = KeyVault.GetSecret("DB-Password")  ✓        │   │
│ │ api_key = KeyVault.GetSecret("API-Key")       ✓        │   │
│ │                                                        │   │
│ │ Secrets stored in Key Vault, not code!                │   │
│ │ Access controlled by RBAC                              │   │
│ │ All access logged                                      │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ AZURE KEY VAULT                                        │   │
│ │                                                        │   │
│ │ Secrets:                                               │   │
│ │ • DB-Password: "MyPassword123" (encrypted)             │   │
│ │ • API-Key: "abc123xyz789" (encrypted)                  │   │
│ │ • SSL-Cert: [certificate data]                         │   │
│ │                                                        │   │
│ │ Only authorized apps can read! ✓                       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 📝 Chapter Summary

✅ **Defense in Depth**
- 7 layers of security (Physical → Data)
- If one layer fails, others protect

✅ **Azure AD**
- Identity management
- SSO (single sign-on)
- MFA (multi-factor auth)
- Conditional Access

✅ **RBAC**
- Owner: Full control
- Contributor: Manage resources, not permissions
- Reader: View only
- Scopes: Management Group → Subscription → RG → Resource

✅ **Azure Policy**
- Enforces standards
- Prevents non-compliant resources
- Different from RBAC (what vs who)

✅ **Defender for Cloud**
- Security score
- Threat protection
- Compliance dashboard

✅ **Key Vault**
- Secure secret storage
- Encryption keys
- Certificates
- Access logged

---

### 🎯 Practice Questions

**Question 1:**
What's the difference between RBAC and Azure Policy?

A) No difference  
B) RBAC controls who can do what, Policy controls what can be created  
C) Policy is for security, RBAC is for compliance  
D) They're the same thing

**Question 2:**
Which RBAC role can create resources but NOT assign permissions?

A) Owner  
B) Contributor  
C) Reader  
D) User Access Administrator

**Question 3:**
What does MFA require?

A) Just a password  
B) Password + something you have (phone/token)  
C) Biometric only  
D) Two passwords

**Question 4:**
Where should you store database passwords?

A) In application code  
B) In a text file  
C) In Key Vault  
D) In a Word document

**Question 5:**
Defense in Depth has how many layers?

A) 3  
B) 5  
C) 7  
D) 10

---

### ✍️ Practice Answers

**Question 1: B** - RBAC controls who, Policy controls what

*Explanation:* This is the KEY difference! RBAC says "John can create VMs" (who can do what). Policy says "VMs must have backup enabled" (what can be created). They work together!

**Question 2: B** - Contributor

*Explanation:* Contributor can create and manage resources but CANNOT assign permissions to others. Only Owner can assign permissions. This is heavily tested!

**Question 3: B** - Password + something you have

*Explanation:* MFA requires two factors: something you know (password) + something you have (phone code/token). This stops hackers who steal passwords.

**Question 4: C** - In Key Vault

*Explanation:* NEVER put secrets in code, files, or documents! Always use Key Vault. It's encrypted, access-controlled, and audited.

**Question 5: C** - 7 layers

*Explanation:* Defense in Depth has 7 layers: Physical, Identity, Perimeter, Network, Compute, Application, Data. Know these for the exam!

---

### 🔖 Quick Reference Card

```
┌──────────────────────────────────────────────────────────────┐
│ SECURITY & GOVERNANCE CHEAT SHEET                            │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ DEFENSE IN DEPTH: 7 layers                                   │
│ Physical → Identity → Perimeter → Network →                  │
│ Compute → Application → Data                                 │
│                                                              │
│ AZURE AD:                                                     │
│ • SSO: One login for all apps                               │
│ • MFA: Password + phone code                                │
│ • Conditional Access: Smart rules                            │
│                                                              │
│ RBAC ROLES:                                                   │
│ • Owner: Everything (including permissions)                  │
│ • Contributor: Resources only                                │
│ • Reader: View only                                          │
│                                                              │
│ RBAC vs POLICY:                                               │
│ • RBAC: WHO can do WHAT                                      │
│ • Policy: WHAT can be created                                │
│                                                              │
│ KEY VAULT:                                                    │
│ • Store: Secrets, keys, certificates                         │
│ • Never put secrets in code!                                 │
│                                                              │
│ DEFENDER FOR CLOUD:                                           │
│ • Security score                                             │
│ • Recommendations                                            │
│ • Threat detection                                           │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**End of Chapter 10** ✓
-e 

---


