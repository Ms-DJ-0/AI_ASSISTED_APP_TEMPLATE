# AI-Assisted App Development Template
> Build with AI intentionally — understand every line, comply with every law.

**Template version 2.0** | Not legal advice — consult a licensed attorney for your situation.

---

## Philosophy

**"Code with AI, not vibe-code."**
AI is a pair programmer, not the architect. You own the code. You are legally responsible for it.
Before shipping any AI-generated code, you must be able to:
1. Explain what it does
2. Audit it for legal and security issues
3. Defend it to a regulator, a client, or a court

This template covers all project types. Jump to the section that matches yours.

---

## Project Type Index

| Project Type | Required Sections |
|---|---|
| Web / Mobile App | Core + Data Privacy + Security Baseline + Pre-Launch |
| SaaS / B2B Platform | Core + Data Privacy + Security Baseline + SaaS/B2B + Pre-Launch |
| Cybersecurity Tool | Core + **Cybersecurity** + Security Baseline + Pre-Launch |
| Healthcare App | Core + Data Privacy + HIPAA + Security Baseline + Pre-Launch |
| Fintech / Payments | Core + Data Privacy + Fintech + Security Baseline + Pre-Launch |
| AI / ML Product | Core + Data Privacy + AI/ML Ethics + Security Baseline + Pre-Launch |
| Developer Tool / CLI | Core + IP/Licensing + Security Baseline + Pre-Launch |
| Children's App | Core + Data Privacy + COPPA + Security Baseline + Pre-Launch |
| Government / Public Sector | Core + Data Privacy + Gov/FedRAMP + Security Baseline + Pre-Launch |
| IoT / Hardware | Core + IoT + Security Baseline + Pre-Launch |

---

## Universal Project Structure

```
my-app/
├── README.md
├── LEGAL.md                    # Filled compliance checklist (see below)
├── LICENSES                    # All third-party dependency licenses
├── SECURITY.md                 # Vulnerability disclosure policy
├── CHANGELOG.md                # Human-maintained, not AI-generated
├── .env.example                # Never commit real secrets
├── src/
│   ├── config/
│   │   └── constants.ts        # App-wide constants, feature flags
│   ├── data/
│   │   └── schema.ts           # Data models — audit every field for PII
│   ├── services/
│   │   └── api.ts              # External calls — audit for data leakage
│   ├── utils/
│   │   └── validation.ts       # Input sanitization — never skip this
│   └── main.ts
├── tests/
│   ├── unit/
│   ├── integration/
│   └── compliance.test.ts      # Tests that encode legal requirements as code
└── docs/
    ├── data-flow.md             # Document what data moves where and why
    ├── threat-model.md          # Required for security tools; recommended for all
    └── architecture.md
```

---

## Core: AI Usage Rules
*Commit this as a team norm. Every project, no exceptions.*

```
RULE 1 — Review before commit.
  No AI output goes into `main` unread. Period.

RULE 2 — No secrets in prompts.
  Never paste API keys, passwords, tokens, or real user data into any AI chat.

RULE 3 — Cite AI-generated files.
  Add at top of file: // AI-assisted — reviewed by [name] on [date]

RULE 4 — Own the logic.
  If you cannot explain a function line by line, do not ship it.

RULE 5 — Validate AI legal claims.
  AI can be confidently wrong about laws. Cross-check with official sources or counsel.

RULE 6 — Delegate the right things to AI.
  Good: boilerplate, tests, refactoring, documentation drafts, regex, migrations.
  Bad: cryptography, payment flows, auth systems, medical logic, security tool core logic.

RULE 7 — AI does not grant legal permission.
  "The AI said it was fine" is not a legal defense. You are responsible.
```

---

## LEGAL.md Template

Copy into your repo and fill out before any public release.

```markdown
# Legal Compliance — [Project Name]
Last reviewed: [DATE] by [NAME]

## Jurisdiction
- Primary market: [US / EU / APAC / Global]
- Governing law: [state/country]
- Entity type: [LLC / Corp / Individual / etc.]

## Data Privacy
- [ ] Privacy policy written, reviewed by counsel, linked in UI
- [ ] PII collected (list every field): [e.g., email, IP address, name]
- [ ] Storage location (country/region): [e.g., AWS us-east-1]
- [ ] Retention policy defined and enforced: [e.g., 90 days then purged]
- [ ] GDPR applicable? → [ ] Cookie consent, [ ] right to erasure implemented
- [ ] CCPA applicable? → [ ] "Do Not Sell My Data" link in footer
- [ ] COPPA: Will any users be under 13? → [ ] Parental consent flow built
- [ ] Data breach notification plan written (72hr GDPR window, state laws vary)

## Security
- [ ] HTTPS enforced, HSTS headers set
- [ ] Secrets in environment variables only — never in code or logs
- [ ] Dependencies audited: `npm audit` / `pip-audit` / `cargo audit`
- [ ] Input validated and sanitized before every DB/API call
- [ ] Authentication uses established library (no homebrew crypto)
- [ ] SECURITY.md (vulnerability disclosure policy) published

## Intellectual Property
- [ ] All dependency licenses listed in LICENSES file
- [ ] No GPL code in a closed-source product
- [ ] AI-generated code reviewed — no verbatim reproduction of likely-copyrighted material
- [ ] App name and logo trademark-searched
- [ ] Domain conflicts checked

## Industry-Specific (fill in what applies — see sections below)
- [ ] Healthcare (HIPAA): [see HIPAA section]
- [ ] Finance (PCI-DSS / SOX): [see Fintech section]
- [ ] Cybersecurity tool: [see Cybersecurity section]
- [ ] AI/ML product: [see AI/ML section]
- [ ] IoT device: [see IoT section]
- [ ] Government contract: [see Gov section]
- [ ] Accessibility (ADA / WCAG 2.1 AA): [ ] Audit completed
```

---

## Section: Cybersecurity Tools
*Applies to: pentest tools, scanners, packet analyzers, exploit frameworks, OSINT tools, security research software, red team utilities, threat intel platforms, SOC/SIEM tools, vulnerability management.*

### The Hard Legal Line

Cybersecurity tools are **dual-use** by definition. The same scanner that finds your vulnerabilities can attack someone else's. Laws do not care about intent — they care about use.

```
Computer Fraud and Abuse Act (CFAA) — US
  Unauthorized access to a computer system is a federal crime.
  "Unauthorized" is defined by the system owner, not you.
  "I was testing security" is not a defense without written permission.

Computer Misuse Act — UK
  Similar scope. Criminal penalties for unauthorized access.

EU Directive on Attacks Against Information Systems
  Member states criminalize unauthorized intrusion tools.

State/local laws may go further than federal law.
```

### Written Authorization — Non-Negotiable

```markdown
## Authorization Checklist (per engagement / per use)

- [ ] Written permission obtained from system OWNER (not just user)
- [ ] Scope defined in writing: which IPs, domains, systems are in-scope
- [ ] Out-of-scope systems explicitly listed
- [ ] Time window authorized: start date/time to end date/time
- [ ] Emergency stop contact identified (who to call if something breaks)
- [ ] Copy of authorization stored securely and retained for [X] years
- [ ] Cloud provider terms reviewed — AWS/GCP/Azure have their own pentest policies
```

**Never assume authorization. Never use "implicit permission." Get it in writing every time.**

### Responsible Disclosure (if your tool finds vulnerabilities)

```markdown
## Disclosure Policy

Follow coordinated disclosure:
1. Report to vendor/owner privately first
2. Give reasonable remediation window (90 days is industry standard — see Google Project Zero)
3. Publish only after patch is available OR window expires
4. Do not publish working exploit code without careful consideration

Bug Bounty programs (HackerOne, Bugcrowd) have their own rules — read them.
CVE assignment: cve.mitre.org
```

### Cybersecurity Tool: Legal Checklist

```markdown
- [ ] Terms of Service clearly state: "For authorized use only"
- [ ] Tool requires explicit user acknowledgment of legal responsibility
- [ ] Tool does NOT auto-scan without user-initiated action
- [ ] No hardcoded targets, no auto-propagation logic
- [ ] Logs kept of tool invocations (for your own legal protection)
- [ ] Export control reviewed: encryption tools may be subject to EAR (US Export Regs)
- [ ] If tool handles malware samples: safe storage, no accidental execution paths
- [ ] If tool does network scanning: rate limits to prevent unintended DoS
- [ ] Vulnerability data storage: encrypted, access-controlled, retention policy set
- [ ] If SaaS: multi-tenant isolation — one customer cannot see another's scan results
```

### Threat Model (required for security tools)

Document this in `docs/threat-model.md`:

```markdown
## Threat Model — [Tool Name]

### Assets
- What does this tool protect or handle? [scan results, credentials, target lists]

### Threat Actors
- Who might misuse this tool, and how?
  - Insider misuse
  - Tool stolen and repurposed
  - API exposed without auth
  - Supply chain compromise of the tool itself

### Attack Surfaces
- Input vectors: [CLI args, config files, network interfaces, APIs]
- Where does untrusted data enter the tool?

### Mitigations
- [List controls for each threat]

### Residual Risk
- [What risk remains and why it's accepted]
```

### AI Prompting — Cybersecurity Specific

```
SAFE — use AI for:
  "Write a Python function to parse Nmap XML output into a structured dict."
  "Generate unit tests for this CVSS score calculator."
  "Write documentation for this network packet struct."
  "Review this regex for detecting SQL injection patterns — flag false positives."

CAREFUL — review every line:
  "Generate a port scanner" → fine, but audit for behavior outside defined scope
  "Write a fuzzer for this protocol" → ensure no unintended side effects

NEVER use AI to generate:
  - Working exploit code targeting real CVEs
  - Credential stuffing or brute-force automation
  - Malware, ransomware, or any self-propagating code
  - Phishing templates targeting real organizations
  - Tools designed to evade specific security products (legal and ethical red line)
```

### Key Legal Resources — Cybersecurity

| Topic | Resource |
|---|---|
| CFAA (US) | justice.gov/criminal-ccips |
| Pentest authorization | SANS Institute authorization templates |
| Responsible disclosure | ISO/IEC 29147, CERT/CC guidelines |
| Bug bounties | hackerone.com/policy, bugcrowd.com/resources |
| Export controls (encryption) | bis.doc.gov/ear |
| CVE program | cve.mitre.org |
| NIST Cybersecurity Framework | nist.gov/cyberframework |
| EU NIS2 Directive | enisa.europa.eu |

---

## Section: Healthcare (HIPAA)

```markdown
- [ ] PHI (Protected Health Information) identified — every field listed
- [ ] PHI encrypted at rest (AES-256 minimum) and in transit (TLS 1.2+)
- [ ] Business Associate Agreements (BAA) signed with every vendor touching PHI
      (AWS, Google Cloud, Twilio, etc. all have BAA programs)
- [ ] Access logging: who accessed what PHI and when
- [ ] Minimum necessary standard: request only the PHI actually needed
- [ ] Breach notification plan: 60-day window to notify HHS and affected individuals
- [ ] No PHI in URLs, logs, error messages, or analytics tools
- [ ] Employee HIPAA training documented
```

---

## Section: Fintech / Payments

```markdown
- [ ] PCI-DSS scope defined — can you reduce it by using Stripe/Braintree tokenization?
- [ ] Card data never stored on your servers unless PCI Level 1 certified
- [ ] SOX applicable (public company)? → Financial data integrity controls documented
- [ ] BSA/AML: Does your app move money? → FinCEN registration may be required
- [ ] Money transmitter licenses: check each state — requirements vary significantly
- [ ] KYC/AML: identity verification required for financial products in most jurisdictions
- [ ] SEC regulations: investment advice features require registration or exemption
```

---

## Section: AI / ML Products

```markdown
- [ ] Training data provenance documented — where did it come from, what license?
- [ ] Bias audit completed for any model making decisions about people
- [ ] EU AI Act classification: what risk tier is this system?
      Unacceptable (banned) / High / Limited / Minimal
- [ ] High-risk AI (employment, credit, healthcare decisions): conformity assessment required
- [ ] Model outputs disclosed as AI-generated where required (deepfakes, synthetic media)
- [ ] Human oversight mechanism exists for high-stakes decisions
- [ ] Data used for training: consent obtained? PII removed or anonymized?
- [ ] Model cards / system cards published for transparency
```

---

## Section: Children's Apps (COPPA / GDPR-K)

```markdown
- [ ] Age gate implemented — how is age verified?
- [ ] No behavioral advertising to users under 13 (COPPA) / under 16 (GDPR)
- [ ] Parental consent mechanism built and tested
- [ ] No PII collected from children without verifiable parental consent
- [ ] Data minimization: collect only what is strictly necessary
- [ ] Parents can request deletion of their child's data
- [ ] No push notifications without parental opt-in
```

---

## Section: IoT / Hardware

```markdown
- [ ] Device firmware update mechanism (OTA) — security patches must be deployable
- [ ] Default passwords forbidden — unique credential per device at manufacture
- [ ] Network traffic encrypted (TLS) — no plaintext protocols
- [ ] Physical access threat modeled — what happens if device is stolen?
- [ ] Data collected by device listed and disclosed
- [ ] End-of-life policy published — how long will you push security updates?
- [ ] FCC / CE / regional hardware certifications obtained
- [ ] California IoT Security Law (SB-327) if selling in CA
```

---

## Section: Government / Public Sector

```markdown
- [ ] FedRAMP authorization required for US federal? (cloud products)
- [ ] FISMA compliance documented
- [ ] Section 508 accessibility compliance (US federal procurement)
- [ ] Data sovereignty: government data may not leave the country
- [ ] ITAR/EAR export controls if defense-adjacent
- [ ] Procurement vehicle identified (GSA schedule, etc.)
```

---

## Section: SaaS / B2B Platforms

```markdown
- [ ] Customer data isolation: multi-tenant architecture audited
- [ ] SLA defined and technically enforceable
- [ ] Data Processing Agreement (DPA) template ready for EU customers
- [ ] Subprocessor list maintained and disclosed (GDPR requirement)
- [ ] SOC 2 Type II: planned or in progress for enterprise sales
- [ ] Penetration test conducted before enterprise launch
- [ ] Incident response plan written and tested
- [ ] Uptime monitoring and status page published
```

---

## AI Prompting Patterns (Universal)

### Boilerplate — safe to delegate:
```
"Generate a [language] function that [specific task].
Include input validation, error handling, and inline comments.
Do NOT implement [specific sensitive logic] — leave a TODO where I will add it."
```

### Compliance audit — AI as reviewer:
```
"Review this code for [GDPR / HIPAA / CFAA compliance issues].
List specific line numbers with concerns.
Flag, do not fix — I will make changes myself."
```

### Test generation — high value:
```
"Write tests for this function covering:
normal input, empty input, maximum length input,
SQL injection attempt, XSS attempt, null/undefined, type mismatch."
```

### Documentation — good use of AI:
```
"Write inline JSDoc comments for this module.
Describe what each parameter is, what can go wrong, and what it returns.
Do not change any logic."
```

### Never delegate to AI alone:
- Cryptography and key management
- Authentication and session logic
- Payment processing flows
- Medical or legal decision logic
- Core security tool logic
- Anything where a bug means a law is broken

---

## Key Legal Resources

| Topic | Resource |
|---|---|
| Data privacy (US) | FTC Act §5, CCPA, state AG offices |
| Data privacy (EU) | GDPR — gdpr.eu |
| Children's data | COPPA — ftc.gov/coppa |
| Accessibility | WCAG 2.1 — w3.org/WAI, Section 508 |
| Healthcare | HIPAA — hhs.gov/hipaa |
| Financial | PCI-DSS — pcisecuritystandards.org |
| Cybersecurity law (US) | CFAA — justice.gov/criminal-ccips |
| AI regulation (EU) | EU AI Act — artificialintelligenceact.eu |
| IoT security (CA) | SB-327 |
| Export controls | bis.doc.gov |
| Open source licenses | choosealicense.com, SPDX |
| Vulnerability disclosure | cve.mitre.org, CERT/CC |

---

## Universal Pre-Launch Checklist

```
LEGAL
[ ] LEGAL.md fully completed and signed off by a responsible person
[ ] Privacy policy and terms of service live at public URLs
[ ] SECURITY.md (vulnerability disclosure) published
[ ] All industry-specific sections above reviewed for this project type

CODE QUALITY
[ ] At least one human has read every AI-generated file
[ ] All AI-generated files have reviewer attribution comment
[ ] `npm audit` / `pip-audit` / `cargo audit` → 0 critical vulnerabilities
[ ] Dependency licenses reviewed — no GPL in closed-source

SECURITY
[ ] HTTPS enforced, HSTS headers present
[ ] No secrets, tokens, or credentials in code or logs
[ ] Error messages show user-friendly text only — no stack traces exposed
[ ] Rate limiting on all public endpoints
[ ] Input validation on every entry point
[ ] Auth and session management uses established library

DATA
[ ] PII inventory complete — every field accounted for
[ ] Logging audited — no passwords, tokens, full card numbers in logs
[ ] Retention policy implemented, not just documented
[ ] Backup and recovery tested

CYBERSECURITY TOOLS (additional)
[ ] ToS requires authorized use only
[ ] User acknowledgment of legal responsibility on first run
[ ] No hardcoded targets or auto-execution behavior
[ ] Authorization template included in documentation
[ ] Threat model completed and reviewed
```

---

*Laws change. This template should be reviewed at least annually and whenever you expand to a new jurisdiction or add a new product category.*
