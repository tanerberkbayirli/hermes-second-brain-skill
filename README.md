# hermes-second-brain-skill

A [Hermes Agent](https://github.com/NousResearch/hermes-agent) skill that makes building and maintaining a **second brain** effortless — for any user, on any machine.

## What it does

Instead of waiting for explicit commands, the skill runs a complete protocol for a persistent markdown "brain file":

- **Onboarding choice (asked first, always):** the user either starts **From Scratch** (nothing is scanned — the brain grows only from what they say) or grants an **explicit scan** of their files, notes and installed apps, from which a draft profile is synthesized and presented for correction before anything is saved.
- **Proactive capture:** durable facts surface in normal conversation ("school starts in 10 days", deadlines, exams, trips) and are written to the brain as dated entries — no "remember this" command needed. Every capture is announced briefly; nothing is recorded silently.
- **Staleness management:** finished events, past deadlines and lived moments automatically move out of the active sections into an **arşiv hatıralar** (memories archive) section, so the active file stays short and current.
- **Dated entries & sections:** every fact carries a date and lives in its matching section (projects, calendar, notes, archive, directions).
- **DIRECTIONS index:** a live table mapping topics → file/folder locations, so "where is X?" is always answerable.
- **Optional encryption:** if the brain file is encrypted (GPG AES256 or similar), it is re-encrypted after every read/write and plaintext copies are deleted. Passphrases are never stored.
- **Weekly review:** a repeatable routine that flags stale projects, archives completed work, prunes past calendar items and verifies the index.

## The hard line

**No scanning without explicit permission.** This is written into the skill as a non-negotiable rule — the scan path only exists as an opt-in the user chooses themselves.

## Install

Copy the skill into your Hermes skills directory:

```bash
git clone https://github.com/tanerberkbayirli/hermes-second-brain-skill.git
cp hermes-second-brain-skill/SKILL.md ~/.hermes/skills/note-taking/second-brain-protocol/
# or, for a named profile:
cp hermes-second-brain-skill/SKILL.md ~/.hermes/profiles/<profile>/skills/note-taking/second-brain-protocol/
```

The skill loads automatically in the next session.

## Author

**TanerBerkB** — built with [Hermes Agent](https://github.com/NousResearch/hermes-agent).

## License

MIT
