---
name: second-brain-protocol
use_when: User captures notes or maintains a second-brain file ('not et').
description: Use when the user captures notes or maintains a brain file.
version: 1.1.0
author: TanerBerkB
license: MIT
metadata:
  hermes:
    tags: [note-taking, second-brain, memory]
    related_skills: [hermes-agent]
---

# Second Brain Protocol

Maintain ONE canonical markdown file as the user's persistent memory. This skill defines how the file is built, written to, and kept alive — it captures facts proactively, not only on command.

## When to Use

- A new user starts using Hermes and wants a second brain set up.
- The user says "not et" / "not al" / "bunu hatırla" / "bunu sonra ilet" or similar.
- New durable facts about the user surface in conversation (events, plans, deadlines, preferences).

## Setup: ask ONE question first

At the very start of building the brain, ask the user to choose one path:

1. **From Scratch** — start empty. Do NOT scan the computer. Ask a few basic questions (name, school/work, goals, ongoing projects) and write only what the user says.
2. **Scan (izinli tarama)** — with the user's explicit permission, examine their files and installed context: notes, documents, folders, calendar-like files, apps they use. Synthesize a profile from what is found and present it for correction before saving. Scan ONLY what the user granted access to; record what was scanned and when.

Never scan without explicit permission, and never mix paths silently — ask, then follow the chosen one.

## Proactive Capture (no command needed)

The brain is not command-driven only. When a durable fact about the user appears in conversation, write it to the brain even without "not et":

- Future events with dates ("10 gün sonra okulu başlıyor" → calendar entry with date).
- Deadlines, exams, appointments, trips.
- Stable preferences, projects, relationships.
- Anything the user asks to remember, remind about, or deliver later.

Rules: dated entry (GG.AA.YYYY), goes into its matching section. Transient/session-only details do NOT get written. Announce briefly what you recorded so the user stays in control — never capture silently.

## Staleness & the Arşiv/Hatıralar section

Facts age. Move stale content OUT of active sections:

- Finished events, past deadlines, passed birthdays → **arşiv hatıralar** section.
- Lived moments and memories the user mentions → **arşiv hatıralar** (dated, one line).
- The active file stays short; arşiv hatıralar grows but never re-enters active sections.

During any update: actively hunt for stale entries (past dates, done events) and move them — don't wait for a weekly review.

## Core Rules

1. **Single file, small file.** One markdown file. If it grows past ~250 lines, move long/finished content to an appendix file and leave a one-line 📎 pointer behind.
2. **Dated entries only.** Every new fact gets a date: `- **GG.AA.YYYY:** ...`.
3. **Everything in its section.** Projects, calendar, notes, arşiv hatıralar, directions. Never append to the bottom; if no section fits, create one.
4. **"Not et" = this file, always.** Explicit notes go straight to the file. Session memory is not enough.
5. **Index table (DIRECTIONS).** Keep a table mapping topics to file/folder locations; add a row when a new location is discovered; use it to answer "where is X".
6. **Encryption (if configured).** If the brain file is encrypted (GPG AES256 or similar), re-encrypt after EVERY read/write and delete the plaintext copy. Never store the passphrase in memory or config — ask the user each session.
7. **Style.** Terse, fact-first. No narrative, no duplication — one fact appears once; update the existing line instead.

## Weekly Review (run on request or via cron)

1. List active projects/events with last-touch dates; flag anything untouched >14 days.
2. Move completed items to arşiv hatıralar.
3. Prune calendar entries now in the past.
4. Verify every DIRECTIONS row still points to an existing path.
5. Report: what was archived, what is stale, one open question.

## Failure Modes to Avoid

- Scanning without explicit permission (hard line).
- Waiting for an explicit "not et" before writing a dated future event.
- Leaving a plaintext copy of an encrypted brain on disk.
- Duplicating a fact that already exists.
- Losing the user's voice: capture their idea verbatim in quotes, analysis in a separate clause.