# Hi, I'm Taisuke

I'm a software engineer building security guardrails and session-reliability tooling for the AI-assisted development era.

## Current focus

- Reliability tooling for long-running AI coding agent sessions (Claude Code ecosystem)
- AI-assisted development security
- Supabase / PostgreSQL / Row Level Security
- Static analysis for database migrations
- DevSecOps guardrails for solo developers and small teams

## Featured OSS

### [agent-session-control-stack](https://github.com/House-lovers7/agent-session-control-stack)

A reference architecture for long-running AI coding agent sessions. Long sessions fail in predictable ways — context bloat, compact-induced state loss, unsafe recovery after summarization. This stack separates the problem into four layers (compression / health detection / checkpointing / recovery) and composes three community projects so they don't fight each other.

- Ships as a Claude Code plugin marketplace — upstream plugins are installed **by reference**, unmodified, with authorship staying upstream
- Includes `/ascs:doctor` (read-only stack diagnosis) and a CI-tested measurement harness with **machine-checked claim boundaries**: the tooling enumerates what the evidence does *not* support
- Publishes its negative results — corrections and void experiments included

```bash
claude plugin marketplace add House-lovers7/agent-session-control-stack
claude plugin install ascs@ascs   # then run /ascs:doctor
```

### [claude-code-session-health](https://github.com/House-lovers7/claude-code-session-health)

Closed-loop token-waste detection for Claude Code: detects cache-re-read bloat in a live session and nudges the model to compact and delegate. Acts as the single compact decider in the stack above.

### [supabase-rls-guard](https://github.com/House-lovers7/supabase-rls-guard)

A tiny, zero-config CLI that statically scans Supabase migration SQL for dangerous Row Level Security mistakes before you ship — missing RLS, dangerous policies, broad grants, views without `security_invoker`, functions without a fixed `search_path`. No database required.
