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

---

## 3. In-scope / Out-scope

- Define in-scope and out-of-scope explicitly (e.g. in scope: Entra ID tenant, one Azure subscription, Key Vault; out of scope: on-prem AD, physical security, HR systems)

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
