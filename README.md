# Personal AI Desktop Assistant

This is a local, privacy-first starter assistant for managing files, reminders,
app launching, document summaries, WhatsApp reply drafts, reports, and action
logs from your laptop.

## What It Can Do

- Search files by name and optional text content.
- Show recently modified files.
- Summarize text, PDF, Word, and Excel files.
- Open apps, folders, URLs, Chrome, Excel, Word, PowerPoint, and WhatsApp Web.
- Draft WhatsApp or email replies for approval.
- Store and list reminders.
- Create a daily work report from local file activity and reminders.
- Organize screenshots by month with confirmation before moving files.
- Keep completed action history in `assistant_logs/actions.jsonl`.

## Setup

Python 3.10 or newer is recommended.

```powershell
python -m pip install -r requirements.txt
```

The core assistant works without the optional packages. Install requirements if
you want PDF, Word, Excel, and image metadata support.

## Common Commands

Search for a resume:

```powershell
python personal_ai.py search resume --root "$env:USERPROFILE"
```

Search inside text files:

```powershell
python personal_ai.py search invoice --root "$env:USERPROFILE\Documents" --content
```

Summarize a document:

```powershell
python personal_ai.py summarize "C:\path\to\file.pdf"
```

Open Chrome, WhatsApp Web, and Excel:

```powershell
python personal_ai.py open chrome whatsapp excel
```

Draft a WhatsApp reply without sending:

```powershell
python personal_ai.py draft-reply --message "Can we schedule a call today?" --tone professional
```

Add a reminder:

```powershell
python personal_ai.py remind "Follow up with client" --when "2026-05-07 10:00"
```

List reminders:

```powershell
python personal_ai.py reminders --open-only
```

Preview screenshot organization:

```powershell
python personal_ai.py organize-screenshots --root "$env:USERPROFILE\Pictures"
```

Move screenshots after confirmation:

```powershell
python personal_ai.py organize-screenshots --root "$env:USERPROFILE\Pictures" --execute
```

Create a daily report:

```powershell
python personal_ai.py daily-report --root "$env:USERPROFILE\Documents" --since today --save
```

Show action logs:

```powershell
python personal_ai.py logs
```

## Safety Rules

- The assistant never sends WhatsApp or email messages.
- Screenshot organization is dry-run by default.
- Moving screenshots requires `--execute` and typed confirmation.
- Sensitive-looking file paths require confirmation before summarization.
- Deletes are not implemented.

## Next Upgrade Options

- Add a voice interface.
- Connect an approved WhatsApp Business API account.
- Add OpenAI or local LLM summarization.
- Add a desktop tray app.
- Add scheduled background checks for reminders and daily reports.
