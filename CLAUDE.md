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
