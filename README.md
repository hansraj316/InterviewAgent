# InterviewAgent

[![Indian Avengers](https://img.shields.io/badge/Managed%20By-Indian%20Avengers-orange?style=flat-square&logo=gitbook)](https://github.com/hansraj316/mission-control-openclaw)
[![Status](https://img.shields.io/badge/Status-Active-4ade80?style=flat-square)](https://github.com/hansraj316/InterviewAgent)
[![Claude Code](https://img.shields.io/badge/Built%20with-Claude%20Code-00d9ff?style=flat-square)](https://claude.ai/claude-code)

> Multi-agent pipeline that automates the end-to-end job application workflow — resume tailoring, cover letter generation, and application submission at scale.

## What It Does

InterviewAgent runs a coordinated pipeline of AI agents to handle the tedious parts of job searching:

1. **Job Discovery** — scrapes and filters job postings matching your criteria
2. **Resume Optimizer** — rewrites your resume to match each job's keywords and requirements
3. **Cover Letter Generator** — writes targeted cover letters using Claude with company/role context
4. **Application Submitter** — fills and submits applications via Playwright browser automation
5. **Tracking & Reporting** — logs every application to Supabase with status, match score, and timestamps

At full throughput: **500+ applications/day**.

## Tech Stack

| Layer | Tech |
|---|---|
| AI / LLM | Claude (Anthropic), MCP tools |
| Orchestration | Claude Code, multi-agent pipeline |
| Browser Automation | Playwright |
| Storage | Supabase (PostgreSQL) |
| Language | Python |

## Architecture

```
Job Sources → Discovery Agent
                    ↓
              Job Queue (Supabase)
                    ↓
         ┌──────────┴──────────┐
   Resume Agent         Cover Letter Agent
         └──────────┬──────────┘
                    ↓
           Submission Agent (Playwright)
                    ↓
           Tracking DB (Supabase)
```

## Quick Start

```bash
# Clone
git clone https://github.com/hansraj316/InterviewAgent
cd InterviewAgent

# Install dependencies
pip install -r requirements.txt
playwright install chromium

# Configure environment
cp .env.example .env
# Set: ANTHROPIC_API_KEY, SUPABASE_URL, SUPABASE_ANON_KEY

# Run
python main.py
```

## Configuration

Edit `config.yaml` to set:
- Job search keywords and location
- Target companies/industries
- Daily application limit
- Resume base file path
- Cover letter tone preferences

## Indian Avengers Context

InterviewAgent is part of the **Indian Avengers** autonomous AI org. It's operated by the **InterviewAgent** sub-agent and monitored via [Mission Control](https://github.com/hansraj316/mission-control-openclaw).

Agent activity is logged to `~/.openclaw/workspace-work/InterviewAgent/autonomy-log.jsonl`.

## License

This project is licensed under the [MIT License](./LICENSE).


## Daily TPM delivery update (2026-04-22)
- Functional: Add adaptive interview flows that adjust question depth by candidate responses
- Non-functional: Expand test coverage for scoring rubric consistency across roles


## Daily delivery update (2026-04-28)
- Functional: Add role-specific interview kit generator with rubric presets
- Non-functional: Improve transcript parsing accuracy for noisy audio inputs
