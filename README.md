# Tazama AI Documentation Project

> **AI-powered documentation system for Tazama** — an open-source, real-time AML and financial fraud detection platform managed by the Linux Foundation and funded by the Bill & Melinda Gates Foundation.

---

## 🧠 What This Project Is

This project uses **Claude AI (Cowork mode)** to transform months of unstructured community Slack conversations into living, structured technical documentation — automatically updated every two days.

No documentation existed for operators deploying Tazama or for beta testers using the hosted sandbox. Questions were being asked repeatedly across Slack channels, answers were buried in threads, and new users had no starting point. This project solves that.

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| **Claude Cowork** | AI agent orchestrating the entire workflow |
| **Slack MCP Connector** | Reading and searching Slack channels via API |
| **Workflow Automation** | Scheduled task (every 2 days) to pull new Slack data and update docs |
| **docx (Node.js)** | Programmatic Word document generation with brand styling |
| **GitHub (Public Repos)** | Source for official Tazama documentation and beta discussions |
| **PPTX Brand Extraction** | Extracted Tazama brand colors and fonts from official presentation files |

---

## 📦 Deliverables

### 1. `Tazama_FAQ.docx`
A branded FAQ document with 25+ Q&A entries across 5 themed sections, sourced entirely from real questions in the `#get-help` Slack channel:

- Platform Architecture & Components
- Deployment & Configuration
- Rules & Typologies
- Database & Data Management
- Troubleshooting & Known Issues

GitHub repos and URLs are bolded in teal throughout for quick scanning.

### 2. `Tazama_Operator_Onboarding_Guide.docx`
A 6-section operator guide covering:

- Platform Overview & Architecture
- Prerequisites & Environment Setup
- Deployment Options (Docker vs Kubernetes)
- Configuration (Rules, Typologies, Network Maps)
- Monitoring & Troubleshooting
- Support & Community Resources

Sections inferred from Slack (not yet officially documented) are marked with visible **"⚠ REVIEW REQUIRED"** callout boxes, so the Tazama team can verify before publishing.

### 3. Auto-Update Scheduled Task
A scheduled task runs every 2 days at 9 AM, reads both Slack channels for new messages, and updates both documents — adding new FAQ entries and creating new sections if new topics emerge that don't fit existing categories.

---

## 🔄 Workflow

```
Slack Channels (#get-help, #tazama-public-beta)
         ↓
  Claude reads & analyzes messages (Slack MCP)
         ↓
  Categorizes recurring themes & questions
         ↓
  Generates structured Q&A entries and guide sections
         ↓
  Builds branded .docx files (Node.js + docx)
         ↓
  Saves to project folder
         ↓
  Scheduled re-run every 2 days (auto-update)
```

---

## 🧩 Product Thinking — What the Data Revealed

Beyond documentation, the Slack analysis surfaced several **product insights** for the Tazama team:

**Recurring user pain points (FAQ-worthy):**
- ArangoDB → PostgreSQL migration confusion (released at v3.0.0 — widely misunderstood)
- NATS vs JetStream misconfiguration (`STARTUP_TYPE=nats` required; JetStream breaks stream naming)
- Docker deployment step-by-step gaps — no authoritative end-to-end guide existed
- Rule processor and typology configuration not documented for self-hosters

**Beta Program 4.0 gaps identified:**
- No end-to-end demo path documented ("send a transaction → see an evaluation result")
- Evaluation results not viewable without database access (API endpoint underdocumented)
- DEMS transaction type field rejects ISO 20022 message format dots (`pacs.008.001.10`)
- TCS mapping save failures (reported by multiple beta testers)

These gaps directly informed a recommendation to the Tazama team to build a dedicated **Beta Sandbox Guide** — a step-by-step walkthrough from sandbox access to first evaluation result, specifically designed for executive demos.

---

## 🎨 Brand Consistency

Tazama brand colors and fonts were extracted directly from official presentation files (PPTX XML parsing) — no manual design work required:

| Element | Value |
|---------|-------|
| Primary Teal | `#006D6F` |
| Light Teal Background | `#D0EAEB` |
| Dark Navy | `#1C2B3A` |
| Body Gray | `#595959` |
| Heading Font | Calibri Light |
| Body Font | Calibri |

---

## 📁 Project Structure

```
Tazama -Claude Projects/
├── README.md                          # This file
├── Tazama_FAQ.docx                    # Branded FAQ (25+ entries)
├── Tazama_Operator_Onboarding_Guide.docx   # 6-section operator guide
└── tazama_docs/
    ├── build_faq.js                   # FAQ document generator
    └── build_guide.js                 # Operator guide generator
```

---

## 💡 Key AI Capabilities Demonstrated

**Slack data mining** — Reading and analyzing hundreds of messages across multiple channels to extract signal from noise.

**Theme clustering** — Grouping free-form questions into logical documentation categories without manual tagging.

**Gap detection** — Identifying what's *missing* from documentation by looking at what users keep asking.

**Hallucination control** — All content traced to verbatim Slack sources. Inferred sections flagged with visible review callouts rather than presented as fact.

**Workflow automation** — Full pipeline from data ingestion → analysis → document generation → delivery, scheduled to run autonomously.

**Brand extraction** — Pulling design tokens (colors, fonts) from binary PPTX files programmatically.

---

## 🤝 About Tazama

Tazama is an open-source platform for real-time AML and financial fraud detection, designed for financial service providers, payment system operators, and regulators. It is hosted by the Linux Foundation and funded by the Bill & Melinda Gates Foundation.

- Website: [tazama.org](https://tazama.org)
- GitHub: [github.com/tazama-lf](https://github.com/tazama-lf)
- Community: [Slack](https://tazama.org/community)
- Beta Testing: [GitHub Discussions](https://github.com/orgs/tazama-lf/discussions/categories/tazama-4-0-0-public-beta-testing)

---

## 👩‍💼 Author

**Shikha** — Product Manager & AI Practitioner

This project demonstrates the use of AI agents for knowledge management, workflow automation, and product insight extraction in a real open-source community context.
