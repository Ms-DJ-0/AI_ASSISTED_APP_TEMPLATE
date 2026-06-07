# AI-Assisted App Development Template

> Build with AI intentionally — understand every line, comply with every law.

---

## What this is

A practical reference template for developers who use AI tools (Claude, Copilot, ChatGPT, etc.) to write code — but want to build responsibly, understand what they're shipping, and stay on the right side of the law.

This is **not** a vibe-coding starter pack. It is the opposite of that.

---

## The core principle

```
AI is a pair programmer, not the architect.
You own the code. You are legally responsible for it.
```

Before shipping any AI-generated code, you must be able to:
1. Explain what it does
2. Audit it for legal and security issues
3. Defend it to a regulator, a client, or a court

---

## Who this is for

- Developers building real products with AI assistance
- Solo builders and small teams who don't have a legal department
- Beginners learning to code with AI who want to build good habits from day one
- Anyone shipping to real users in a regulated environment

---

## What's inside

| File | Purpose |
|---|---|
| `AI_ASSISTED_APP_TEMPLATE.md` | The full template — read this |
| `README.md` | This file |

### The template covers

**Universal**
- Project structure that works for any stack
- 7 core AI usage rules to commit as a team norm
- `LEGAL.md` template — fill out before every release
- AI prompting patterns (what to delegate, what to own)
- Universal pre-launch checklist

**By project type**
- Web / Mobile App
- SaaS / B2B Platform
- **Cybersecurity Tools** ← most detailed section
- Healthcare (HIPAA)
- Fintech / Payments
- AI / ML Products
- Children's Apps (COPPA / GDPR-K)
- IoT / Hardware
- Government / Public Sector
- Developer Tools / CLI

---

## Quick start

1. Copy `AI_ASSISTED_APP_TEMPLATE.md` into your repo
2. Find your project type in the **Project Type Index**
3. Create `LEGAL.md` from the template and fill it out
4. Create `SECURITY.md` (vulnerability disclosure policy)
5. Add `DEVLOG.md` — one entry per coding session (see workflow below)

---

## The workflow this pairs with

This template assumes you follow a deliberate AI coding workflow — not copy-paste from AI chat.

```
1. Understand the problem before opening any editor
2. Ask AI to explain concepts, not deliver code
3. Interrogate AI output before accepting it
4. Type the code yourself — adapt, don't paste
5. Break it on purpose and fix it yourself
6. Commit with messages that reflect decisions, not just actions
7. Write a 4-line debrief in DEVLOG.md after every session
```

**The five-question gate** — answer these before accepting any AI-generated code:
- Can I explain every line of this?
- Does this match my specific design, or is it generic?
- Where does it break? (resize, empty input, bad data)
- What would I name things differently?
- What's missing that AI assumed away?

If you can't answer them, go back and understand it first.

---

## Cybersecurity note

The cybersecurity section is the most detailed in this template because the legal exposure is the highest. Key points:

**Authorization is non-negotiable.** Written permission from the system owner before every use. Not just from the user — from the owner. "I was testing security" is not a legal defense without it.

**Dual-use liability.** The CFAA (US), Computer Misuse Act (UK), and EU Directive on Attacks Against Information Systems don't care about your intent — they care about use. Build accordingly.

**What AI should never generate for security tools:**
- Working exploit code targeting real CVEs
- Credential stuffing or brute-force automation
- Malware, ransomware, or self-propagating code
- Tools designed to evade specific security products

---

## Legal disclaimer

This template is **not legal advice**. It is a practical starting point based on publicly available regulatory frameworks. Laws vary by jurisdiction and change over time.

Consult a licensed attorney before shipping to real users, especially in regulated industries (healthcare, finance, government).

> ⚠️ Review this template at minimum annually and whenever you expand to a new jurisdiction or product category.

---

## Contributing

Found an error, outdated law reference, or missing project type? Open an issue or PR. Legal landscape changes — this should too.

When contributing:
- Cite the specific law, regulation, or official guidance you're referencing
- Note the jurisdiction it applies to
- Flag if something has a sunset date or is pending enforcement

---

## License

MIT — use freely, adapt for your own projects, no attribution required.

---

*Built with AI assistance. Every line reviewed by a human.*
