# 1. Scope / Scenario

I've chosen fictitious financial services for this, as it occured to me the most important reasoning behind these controls and environment set up is the **why**.
This is the case sceanario:

- A mid-tier UK retail and commercial bank, holding a banking licence, **dual-regulated by the FCA and PRA**.
- Offers current accounts, savings, and commercial lending; issues debit cards, which pulls **PCI DSS** into scope for anything touching card data.
- Small in-house technology and security function, reflecting a realistic mid-tier headcount rather than a Tier 1 bank's resources. Pragmatic, risk-based choices over "buy every tool" approach, there is no unlimited budget.
- An internal audit found excessive standing privileged access and weak segregation of duties triggering this remediation programme.

---
ToDo:

## 2. Key Objectives / Success Criteria

- Define objectives and success criteria - what will exist, and how I'll know each phase actually worked

[Phase 0: Scope] - Define the scope, problem scenario, and propose plan of action.

[Phase 1 - Entra ID Foundation] - Stand up the tenant, licensing, baseline population, and the account-tiering model everything else in the project sits on.

[Phase 2: Conditional Access] - Enforce strong authentication and define trust zones, with privileged access held to a visibly higher bar than standard access.

[Phase 3: PIM - Entra roles] - Move from standing role assignments to eligible, time-bound, justified, approved activation - and prove it actually works end to end.

[Phase 4: Identity Governance] - Move from one-off correct configuration to demonstrable, recurring assurance that access stays correct over time.

| Question | Standard Policy & Best Practice |
|---|---|
| Who is allowed | Only identities with a documented business need. Standard daily accounts should never hold active administrative privileges. Admins use standard accounts for daily work (email, web browsing) and elevate using dedicated secondary accounts (admin_username) or PIM for Groups. |
| Why are they allowed? | Access is granted based on the Principle of Least Privilege. Users are assigned Eligible status rather than permanent Active status. To activate, they must provide a valid business reason (e.g., Change Request / Incident Ticket ID). |
| When/How long? | Access is strictly Just-In-Time (JIT).- Standard IT Roles: 4 to 8 hours max.- Tier 0 Roles (Global Admin, etc.): 1 to 4 hours max with mandatory manager/security approval.- Eligibility Duration: Users are assigned Eligible status for a maximum of 6–12 months, requiring periodic Access Review renewals. |

[Phase 5: Azure Environment] - Stand up the Azure footprint the vault, rotation, and Cloud PAM scenarios need, with least-privilege RBAC from the start rather than retrofitted later.

[Phase 6: Digital Vault] - Centralise secrets in Azure Key Vault, and control who and what can reach them with the same eligible/active discipline as everything else - not a separate, softer standard for "just secrets".

[Phase 7: PAW / JIT Infra] - Show how a privileged user actually reaches a system to do privileged work, rather than stopping at "here's where the credential lives". (Dependant on Bastion costs)

[Phase 8: Credential Rotation] - Show that secrets don't sit static once vaulted - rotation is scheduled, automated where possible, and eliminated entirely where a managed identity can replace it. Lifecycle.

[Phase 9: Cloud PAM Scenarios] - Realistic, end-to-end scenarios a real bank would actually face. Test the system.

[Phase 10: Logging deep-dive] - Turn the log data that's been flowing since Phase 1 into genuine, query evidence and a reviewable dashboard.

[Phase 11: Break-glass showcase] - Prove the emergency-access process works under simulated pressure, with the same rigour and audit trail as everything else - break-glass access should be rare, alarmed, and reviewed, not a quiet backdoor you barely notice being accessed.

[Phase 12: Security Testing] - Break and detect issues in what you made, not just implement controls. Users requesting access without the qualifiers, stale accounts and access reviews, excessive privilege, legacy auth attempts against protected assets, PIM approver denies access successes, short reports.
  

---

## 3. In-scope / Out-scope

- In scope: Entra ID tenant, one Azure subscription, Key Vault
- Out of scope: on-prem AD, physical security, HR systems

---

## 4. Architecture Diagram

- logical identity architecture diagram: tenant, account tiers, group structure, PIM-eligible roles

---

## 5. Trust-Zone Diagram

- trust-zone diagram: named locations, Conditional Access zones, what's trusted vs untrusted

---

## 6. Current-State VS Target-State
- current-state vs target-state diagram  (simple one - "before: N standing admins, 0 MFA enforcement" vs "after: 0 standing admins, PIM-eligible only, MFA everywhere")

---

## 7. Regulatory Map

- Build the regulatory mapping table

---

<!-- - 8. Add a short RAID log (Risks, Assumptions, Issues, Dependencies)  -->
