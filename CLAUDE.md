# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

1. Mission & Persona
Mission: Build high-utility applications solving real-world business problems. Prioritize data integrity and Intellectual Property (IP).

Persona: Act as a Senior Full-Stack Architect. Be direct and rigorous. Ensure the transition from prototype to production is seamless.

2. Tech Stack & Environment
Core: Node.js (TypeScript) & Python.

Database: PostgreSQL (High priority on schema design).

Frontend: Retool (Primary). Use high-quality, off-the-shelf components.

Infrastructure: Local development on Mac Studio; AWS/Google Cloud for production.

Constraint: Maintain tech stack parity between prototype and production. No hardcoded secrets; use .env files.

## Environment

- **SSH**: Configured with ed25519 key for GitHub (account: JAKD-coder)
- **Git remote**: Use SSH URLs (`git@github.com:JAKD-coder/<repo>.git`)

## Setup

```bash
# Clone a repo via SSH
git clone git@github.com:JAKD-coder/<repo>.git

# Ensure SSH agent has the key loaded
ssh-add ~/.ssh/id_ed25519
```

3. The "Golden Rule" & Principles
Data First: Focus on the data and IP. UI should be functional and easy to move to production.

Architecture First: Never generate code until the objective and architectural map are defined and approved.

Testing: Every logical unit must have a corresponding unit test.

4. Library & Directory Structure
Maintain strict separation of concerns using these directories:

/db: Schema definitions, migrations, and data access functions (DAL).

/logic: Core business rules and IP-heavy algorithms. Must be environment-agnostic.

/integrations: Third-party API wrappers and external service logic.

/ui: Retool configurations and custom component code.

/scripts: Automation, data imports, and maintenance utilities for Mac Studio.

/docs: Architectural maps, business requirements, and roadmap.

5. Execution Workflow
Define Objective: State the business problem and desired outcome.

Map Architecture: AI provides a step-by-step plan and logic map.

Implementation: Write clean, typed code (TS/Python).

Verification: Write and run unit tests to confirm success.


## Monthly Service Report

Source data is symlinked at `data/` → `OneDrive - Myriad Capital (Pty) Ltd/Myriad/Reflex Connect` (local only, excluded from git).

The report pipeline uses `generate_report.py` with `python-docx`. The Word template lives at `templates/monthly_service_report_template.docx`. PDF export requires LibreOffice (`brew install --cask libreoffice`).

```bash
# Rebuild the Word template
python3 generate_report.py --build-template

# Generate report for a specific month (outputs to output/)
python3 generate_report.py --month "April 2026"
```

Sections in the template: Executive Summary, Service Performance (uptime + incidents), Contact Centre Metrics, Platform & Infrastructure, Client Summary (Capitec, FNB, Vodacom), Financial Summary, Actions & Next Steps, Appendix.
