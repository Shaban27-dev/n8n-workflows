# n8n Workflows Portfolio

![n8n](https://img.shields.io/badge/platform-n8n-FF6D5A?style=flat-square&logo=n8n)
![Workflows](https://img.shields.io/badge/workflows-4%20and%20growing-brightgreen?style=flat-square)
![Status](https://img.shields.io/badge/status-actively%20maintained-blue?style=flat-square)
![Focus](https://img.shields.io/badge/focus-production--ready-orange?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)

A curated collection of production-ready n8n workflows, each built to solve a real operational problem. This repository is not a showcase of what n8n can do — it is a record of automations that have been designed, tested, and structured to the standard of software that a business could actually deploy and rely on.

---

## About

Most workflow repositories are collections of demos. This one is different.

Every workflow in this repository starts from a real problem — a repetitive manual task that consumes time, introduces error, or creates invisible operational gaps. The automation is designed to eliminate that task entirely, not just reduce the friction around it.

The engineering philosophy that runs through every project here:

- **Production-ready** — workflows are tested against live data, handle edge cases, and include error paths. They are not prototypes.
- **Modular** — each node has a single responsibility. Pipelines are structured so that individual components can be swapped, extended, or reused without rebuilding the whole.
- **Documented** — every workflow ships with a README explaining the business problem, the architecture, the tech stack, and a step-by-step execution walkthrough. Someone new to the project should be able to understand it in minutes.
- **Business-focused** — the success criteria for each workflow is operational impact, not technical complexity. The simplest implementation that solves the problem reliably is the right one.

---

## Repository Highlights

- **Event-driven automations** — workflows that react instantly to triggers rather than running on polling cycles
- **Scheduled automations** — time-based pipelines that run unattended on a configurable frequency
- **RSS feed ingestion** — continuous article monitoring from AI industry news sources on a four-hour polling cycle
- **AI-powered summarization** — LangChain AI Agent with OpenRouter LLM generating structured executive summaries and impact analysis per article
- **Dual-pipeline architecture** — independent ingestion and delivery schedules sharing a Notion knowledge base as the persistence layer
- **Knowledge base automation** — a queryable Notion database built continuously from RSS monitoring with no manual curation
- **Form-triggered pipelines** — intake workflows that fire the moment a prospect submits an inquiry form
- **CRM integration** — structured lead records written directly to Notion on every submission
- **Lead qualification logic** — JavaScript-based scoring rules that classify and route leads automatically
- **Google Workspace integrations** — Drive, Sheets, and Gmail connected as first-class workflow components
- **Web scraping pipelines** — HTTP requests, HTML extraction, and live data validation
- **Conditional routing** — Switch nodes and IF gates that branch execution based on data rather than fixed paths
- **JavaScript Code nodes** — custom logic for data transformation, scoring, HTML assembly, and metadata formatting
- **HTML email notifications** — branded, structured email templates for client-facing, internal, and digest communications
- **Audit logging** — persistent, append-only records of every workflow execution in Google Sheets or Notion
- **Exportable JSON** — every workflow ships as an importable `.json` file, deployable in any n8n instance

---

## Featured Workflows

| Workflow | Problem Solved | Technologies | Docs |
|---|---|---|---|
| 🔔 [Price Drop Notifier](./price-drop-notifier/) | Monitors a product page daily and sends an email alert the moment the price drops to a configured target | n8n · HTTP Request · HTML Extraction · IF · Gmail | [README](./price-drop-notifier/README.md) |
| ⚙️ [Drive File Organizer](./drive-file-organizer/) | Detects new Google Drive uploads, classifies them by extension, moves them to the correct folder, logs every action to Sheets, and sends a confirmation email | n8n · Google Drive · Switch · JS Code · Google Sheets · Gmail | [README](./drive-file-organizer/README.md) |
| 📋 [Client Form → CRM](./client-form-crm/) | Captures client inquiries from Typeform, scores leads against business rules, logs every submission to Notion, and routes prospects into three distinct automated email paths | n8n · Typeform · Set · JS Code · Notion · Switch · Gmail | [README](./client-form-crm/README.md) |
| 📰 [AI News Digest Automation](./ai-news-digest-automation/) | Monitors the AI industry RSS feed every four hours, generates LLM-powered summaries via OpenRouter, stores every article in a Notion knowledge base, and emails a curated executive briefing at 8 AM daily | n8n · RSS Feed · HTTP Request · JS Code · AI Agent · OpenRouter · Notion · Gmail | [README](./ai-news-digest-automation/README.md) |

---

## Repository Structure

```
n8n-workflows/
│
├── assets/
│   ├── email-notification.png
│   ├── featured-workflow.png
│   ├── repo-overview.png
│   └── sheets-log.png
│
├── ai-news-digest-automation/
│   ├── ai-news-digest-automation.json   # Importable n8n workflow
│   ├── README.md
│   └── images/
│       ├── workflow.png
│       ├── notion-database.png
│       └── daily-news-email.png
│
├── client-form-crm/
│   ├── client-form-crm.json             # Importable n8n workflow
│   ├── README.md
│   └── images/
│       ├── workflow.png
│       ├── notion-crm.png
│       ├── high-budget-email.png
│       ├── low-budget-email.png
│       └── missing-info-email.png
│
├── drive-file-organizer/
│   ├── drive-file-organizer.json        # Importable n8n workflow
│   ├── README.md
│   └── images/
│       ├── workflow.png
│       ├── email-alert.png
│       └── google-sheet.png
│
├── price-drop-notifier/
│   ├── price-drop-notifier.json         # Importable n8n workflow
│   ├── README.md
│   └── images/
│       ├── workflow.png
│       └── email-alert.png
│
├── LICENSE
└── README.md
```

Each workflow folder is self-contained: the exported `.json` file, the documentation, and all reference screenshots live together. Import the JSON, connect credentials, and the workflow is ready to activate.

---

## Technologies Used

| Technology | Role Across Workflows |
|---|---|
| **n8n** | Orchestration engine — hosts, schedules, and executes all workflows |
| **RSS Feed Trigger** | Polls AI industry RSS sources on a four-hour interval and fires one execution per new article |
| **AI Agent (LangChain)** | Orchestrates structured LLM calls with constrained prompt formatting for consistent, professional output |
| **OpenRouter LLM** | Language model backend — generates article summaries and industry impact bullet points |
| **Typeform Trigger** | Form submission listener — fires the intake pipeline immediately on new client inquiry |
| **Google Drive** | File detection via trigger and programmatic file moves between folders |
| **Google Sheets** | Append-only audit log for workflow execution records |
| **Notion** | Knowledge base and CRM destination — stores AI article summaries and client lead records with full structured data |
| **Gmail** | Outbound HTML email delivery for alerts, confirmations, client responses, digest briefings, and error notifications |
| **HTTP Request** | Live data fetching from external URLs and APIs |
| **HTML Extraction** | CSS-selector-based parsing of web page content |
| **Switch Node** | Rules-based routing that branches execution by file type, lead status, or data value |
| **IF Node** | Binary conditional gates for data validation and threshold checks |
| **Set Node** | Field normalization — remaps raw form labels to consistent keys for downstream processing |
| **JavaScript Code Node** | Custom data transformation, lead scoring logic, HTML digest assembly, and metadata formatting |
| **HTML Email Templates** | Branded, structured email layouts — client-facing responses, internal priority alerts, and daily digest briefings |
| **Schedule Trigger** | Time-based workflow initiation without external cron management |

---

## Why These Projects?

Every business runs on repetitive processes. Someone checks a spreadsheet every morning. Someone moves files from one folder to another. Someone refreshes a product page hoping a price changed. Someone manually reads a form submission, copies the details into a CRM, decides whether the lead is worth pursuing, and types the same reply they've typed a hundred times before. Someone opens five different websites each morning trying to stay current with a fast-moving industry.

These tasks are not difficult — they are just consistent, predictable, and time-consuming in a way that scales badly. The larger the operation, the more of them exist, and the more they crowd out work that actually requires human judgment.

Automation handles the predictable. This repository is a record of what that looks like in practice: real triggers, real data, real integrations, and outcomes that free up time rather than just demonstrating that automation is possible.

The goal for each workflow is the same — that after it runs, a person's default assumption is that the task is handled, not that they need to go check.

---

## Upcoming Projects

The workflows currently in this repository are the foundation. The roadmap extends in two directions: deeper integrations with the tools businesses already use, and AI-augmented workflows that go beyond conditional routing.

| Project | Description | Status |
|---|---|---|
| 🤖 AI Lead Enrichment Pipeline | Webhook-triggered lead intake with Claude AI scoring, Google Sheets logging, and Slack alerts | In progress |
| 📄 Invoice OCR Processing | Email attachment detection, OCR extraction, structured data logging, and accountant notification | Planned |
| 📬 AI Email Classifier | Inbox monitoring with LLM-based label assignment and auto-routing to the right team | Planned |
| 🧑‍💼 Customer Onboarding Workflow | Post-signup pipeline: welcome email → task creation → CRM update → team notification | Planned |
| 📊 Multi-Channel Job Alert System | Job board scraping with deduplication, Sheets logging, and digest email delivery | Planned |
| 📱 Social Media Automation | Scheduled post publishing across platforms from a content calendar | Planned |

---

## Quick Start

Every workflow in this repository exports as a self-contained JSON file. To run one:

**1. Download the workflow JSON**

Navigate to any workflow folder and download the `.json` file.

**2. Import into n8n**

Open your n8n instance → **Workflows** → **Import from file** → select the downloaded JSON.

**3. Connect credentials**

The workflow will prompt for any required credentials (Google account, Gmail, Notion, Typeform, OpenRouter, etc.). Connect them through n8n's credential manager.

**4. Configure parameters**

Review the workflow's README for any variables that need updating — folder IDs, target prices, email addresses, form IDs, database IDs, or RSS feed URLs.

**5. Activate**

Toggle the workflow to **Active**. It begins running immediately on its configured trigger.

> Each workflow's README contains a full deployment walkthrough specific to that project.

---

## Screenshots

### Repository Overview

> ![Repository](assets/repo-overview.png)

The `Shaban27-dev/n8n-workflows` repository on GitHub, showing the four current workflow folders and clean commit history.

---

### Workflow Example — Drive File Organizer

> ![Workflow](assets/featured-workflow.png)

The Drive File Organizer pipeline in the n8n editor, showing the Google Drive Trigger, Switch node branching paths, and the converged logging and notification pipeline downstream.

---

### Email Notification

> ![Email](assets/email-notification.png)

A live confirmation email from the Drive File Organizer. The "CORE AUTOMATION ENGINE" status badge, structured file detail table, and green pipeline route indicator are all rendered by a custom HTML template.

---

### Google Sheets Audit Log

> ![Sheets](assets/sheets-log.png)

The `File Organizer Logs` spreadsheet maintained by the Drive File Organizer. Each row is an append from a single workflow execution, building a persistent, queryable record of every file processed.

---

## About Me

**Shaban Alam**
Python Automation Developer · n8n Workflow Specialist · AI Automation Builder

I build automation systems for businesses that want to stop doing things manually. My focus is on production-ready workflows — not demos, not prototypes, but systems that run reliably in the background and deliver measurable operational value.

- **GitHub:** [github.com/Shaban27-dev](https://github.com/Shaban27-dev)
- **Email:** shabandev27@gmail.com
- **Available for:** freelance automation projects, workflow consulting, Google Workspace integrations, CRM automation, AI pipeline development

---

## Freelance Services

If you have a manual process that runs on a predictable pattern, it can probably be automated. Here is what I build:

| Service | Description |
|---|---|
| **n8n Workflow Development** | Custom workflow design, build, and deployment for any trigger-action automation |
| **AI Workflow Automation** | LLM-powered pipelines using Claude or OpenAI for classification, enrichment, and generation |
| **AI Content Pipelines** | RSS monitoring, LLM-powered summarization, knowledge base construction, and scheduled digest delivery |
| **CRM Automation** | Form-to-CRM pipelines with lead scoring, qualification routing, and automated client communication |
| **Google Workspace Automation** | Drive, Sheets, Gmail, and Calendar integrated into operational workflows |
| **API Integration** | Connecting internal tools and third-party APIs through webhook and HTTP request pipelines |
| **Python Automation** | Script-based automation for data processing, scraping, scheduling, and reporting |
| **Business Process Automation** | End-to-end replacement of repetitive manual workflows with event-driven systems |
| **Custom Internal Tools** | Lightweight automation tools built for specific operational needs |
| **Workflow Optimization** | Audit and refactor of existing n8n or Python workflows for reliability and performance |

> **Interested in working together?** Reach out at shabandev27@gmail.com with a brief description of the process you want to automate.

---

## Summary

This repository is an actively growing portfolio of automation systems built around one principle: every workflow should solve a problem a real business actually has, and solve it in a way that is reliable enough to run without supervision.

The projects here draw on event-driven architecture, RSS-driven content intelligence, AI-powered summarization, dual-pipeline scheduling, form-triggered intake pipelines, CRM integration, Google Workspace automation, web scraping, and conditional workflow orchestration — applied to problems that repeat themselves every day in organizations of every size. Each one is documented, exportable, and ready to deploy.

This repository is actively maintained with new production-ready workflows added regularly. Star the repository to stay updated.
