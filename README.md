# AI Compliance Transaction Monitoring System

An agentic AI system that autonomously monitors financial transactions 
for suspicious activity, generates risk assessments, and produces 
professional compliance reports — built to demonstrate applied AI 
skills in a regulated financial environment.

---

## Project Overview

This project simulates a real-world compliance monitoring workflow 
at a financial institution. Drawing on experience in transaction monitoring during 
a compliance internship, I designed and built an end-to-end agentic 
AI pipeline that mirrors how modern financial institutions are beginning 
to augment their compliance operations with AI.

All transaction data is entirely synthetic and generated programmatically. 
No real individuals or financial institutions are represented.

---

## What Makes This Agentic

Unlike generative AI, which responds to a single prompt, this system 
operates autonomously across multiple steps without human intervention 
at each stage:

1. **Ingest** — loads and parses 500 synthetic transactions
2. **Detect** — applies 7 rule-based flags, including failed transaction monitoring
3. **Investigate** — calls Claude API independently for each flagged case
4. **Assess** — assigns risk scores with written compliance justifications
5. **Report** — generates two professional PDF outputs for different stakeholders

The agent handles errors gracefully — timing out cases are automatically 
routed to a manual review queue rather than silently failing.

---

## Compliance Features

- **KYC gap detection** — flags transactions where passport documentation is missing
- **Structuring detection** — identifies rapid succession transactions from the same sender
- **Failed transaction monitoring** — catches suspicious failed attempts, not just completed transactions
- **Risk-tiered reporting** — Critical, High, Medium, and Low risk classifications
- **Deduplication logic** — prevents the same case from appearing in multiple queues
- **Manual review routing** — unassessed cases are escalated automatically

---

## Output Reports

| Report | Purpose | Audience |
|---|---|---|
| Full Compliance Report | Complete audit trail of all 77 flagged transactions | Regulators, Senior Management, Internal Audit |
| Daily Triage Report | Priority actions for today — Critical and missing KYC only | Compliance Analysts |

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas | Data manipulation |
| Faker | Synthetic data generation |
| Anthropic API (Claude Haiku) | AI risk assessment |
| ReportLab | PDF report generation |
| Google Colab | Development environment |

---

## Project Structure
```
ai-compliance-monitoring/
├── AI_Transaction_Monitoring_System.ipynb  # Full notebook — all stages
├── transactions_agent_view - transactions_agent_view.csv        # Synthetic transaction dataset
├── compliance_report.pdf              # Full investigation report
└── daily_triage_report.pdf           # Daily triage report
```

---

## Key Design Decisions

**Why two reports?**
Compliance teams face constant backlogs. A 40-page document reviewed 
daily is operationally unrealistic. The triage report surfaces only 
what needs action today, while the full report serves as the audit trail.

**Why monitor failed transactions?**
In compliance, intent matters as much as outcome. A criminal attempting 
to move £80,000 doesn't become less suspicious because the transaction 
failed. Failed transaction monitoring is explicitly referenced in NCA 
guidance on SAR filing.

**Why higher thresholds for failed transactions?**
At scale, a bank processes thousands of daily transactions. Flagging 
every failed transaction would overwhelm analysts with noise. Higher 
thresholds ensure the alert-to-investigation ratio remains operationally 
viable.

---

## How to Run

1. Open `AI_Transaction_Monitoring_System.ipynb` in Google Colab
2. Add your Anthropic API key to Colab Secrets as `ANTHROPIC_API_KEY`
3. Mount Google Drive when prompted
4. Run all cells in order from top to bottom

---

*Built as a portfolio project to demonstrate applied agentic AI skills 
in a compliance context. All data is synthetic.*
