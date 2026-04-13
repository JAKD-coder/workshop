# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

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
