# 🧠 AI Meeting Minutes Suite – Intelligent Meeting Documentation FREE API

## Transform Raw Notes into Professional Meeting Minutes in Seconds

The **AI Meeting Minutes Suite** is an all-in-one API built to **automate your meeting documentation process**.  
Powered by an **advanced AI model trained on billions of business texts and best practice templates**, it instantly turns your meeting notes into clear, structured, and actionable **minutes, summaries, and reports** — all while keeping your data safe.

<p align="center">
  🆓 <b>FREE API</b> — use instantly on 
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-meeting-minutes-suite-summaries-templates-redaction" target="_blank"><b>RapidAPI</b></a> 🚀
</p>

<p align="center">
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-meeting-minutes-suite-summaries-templates-redaction">
    <img src="logo.png" width="120" alt="AI Meeting Minutes Suite API Logo">
  </a>
</p>

---

## 🚀 Key Features

### 📝 **Instant AI Meeting Minutes**
Convert any plain text or markdown notes into professional, formatted minutes — including:
- Title, date, facilitator, and attendees
- Discussion summaries
- Decisions & blockers
- Action items with owners and deadlines

### 🎨 **Custom Templates & Styles**
Choose from multiple output templates and tones:
- **Strict format** — corporate or board-ready  
- **PM-style** — project-oriented summaries with next steps  
- **Executive summary** — concise, high-level insights  
- **Brief mode** — lightweight, fast summaries  

You can preview template layouts before generating the full document.

### 🌍 **Multilingual & Smart Translation**
- Auto-detects and supports multilingual input (English, Spanish, German, French, Russian, and more).  
- Ensures the final output is fully unified in your chosen **output_language**.

### 🧬 **Built-In Data Privacy & Redaction**
- Automatically **masks PII data** such as emails, phone numbers, and URLs when requested.  
- **Local redaction** ensures sensitive information never leaves your system in plain form.

### 🔒 **Privacy & Security by Design**
We value your trust:
- **No data storage:** Inputs are processed in memory only — nothing is stored in a database.  
- **No content logging:** Meeting content is never logged or reused.  
- **Stateless & isolated requests:** Each request is self-contained and fully ephemeral.  
- **Enterprise-grade HTTPS** encryption ensures your data remains private.

### ⚙️ **Flexible Modes & Controls**
Fine-tune the output via `controls`:
```json
{
  "output_language": "English",
  "template": "pm",
  "tone": "concise",
  "redact_pii": true,
  "normalize_dates": true,
  "bullets_style": "dash"
}
```

---

## 💡 Example Use Cases
- Internal meeting minutes generation for distributed teams  
- Client call summaries and follow-up action plans  
- Automated PM documentation and sprint summaries  
- Secure transcription cleanup with PII redaction  

---

## 📦 Endpoints Overview

| Endpoint | Description |
|-----------|--------------|
| **POST /generate** | Generate structured meeting minutes instantly |
| **POST /redact** | Run PII masking and sanitization on notes |
| **POST /template-preview** | Preview how chosen settings render in markdown |

---

## 🛡️ Why Developers Love It

✅ Secure — no database or data logging  
✅ Fast — synchronous generation for short to medium notes  
✅ Compatible — returns clean JSON or Markdown for easy integration  
✅ Flexible — supports all major languages and templates  
✅ Reliable — AI model fine-tuned for clarity, precision, and context  

---

## 🔧 Example Integration

```bash
curl -X POST "/generate.php" \
-H "Content-Type: application/json" \
-H "X-RapidAPI-Key: YOUR_API_KEY" \
-d '{
  "raw_notes": "Project kickoff meeting notes...",
  "controls": {
    "output_language": "English",
    "template": "pm",
    "tone": "concise",
    "redact_pii": true
  }
}'
```

---

## 🤝 Trust, Transparency & Safety

We believe in **responsible AI**:
- Your meeting data stays **yours**.
- The API does **not store**, **cache**, or **share** any user content.
- Each request is securely processed in real-time and discarded immediately.

---

## 📚 Summary

**AI Meeting Minutes Suite** empowers professionals, developers, and teams to:
- Eliminate manual note-taking
- Generate consistent meeting documentation
- Safeguard confidential data with confidence  

&gt; Start automating your meeting minutes today — securely, intelligently, and instantly.

---

# 🧠 AI Meeting Minutes Suite — API Documentation

## Overview
The **AI Meeting Minutes Suite** is a professional API designed to transform raw meeting notes into structured, multilingual, and secure meeting documentation. It offers instant generation of minutes, PII redaction, and customizable template previews — all powered by an advanced AI model trained on billions of real-world business texts.

All endpoints are **synchronous**, **stateless**, and **secure** — your data is never stored or logged.

---

## 🚀 API Endpoints Summary

| Endpoint | Description |
|-----------|--------------|
| **POST /generate.php** | Generate structured meeting minutes instantly. |
| **POST /redact.php** | Run PII masking and sanitization on notes. |
| **POST /template-preview.php** | Preview how chosen settings render in Markdown. |

---

## 🧩 1. POST /generate.php — Generate AI Meeting Minutes

### Description
Turn raw meeting notes (plain text or markdown) into **structured minutes** and **ready-to-paste Markdown**. Supports templates, tone, multilingual output, date normalization, and optional PII redaction.

### Headers
```http
Content-Type: application/json
```

### Body (top-level)
| Name | Type | Required | Description |
|---|---|---|---|
| `raw_notes` | string | **Yes** | Plain text or Markdown input; ~20–60k chars in sync mode. Supports markers like `Agenda:`, `Decisions:`, `Action Items:`. |
| `meeting_meta` | object | No | Optional metadata that improves quality. See table below. |
| `controls` | object | No | Generation controls (language, template, tone, PII, etc.). See table below. |

### `meeting_meta`
| Name | Type | Required | Description |
|---|---|---|---|
| `title` | string | No | Meeting title. |
| `date` | string | No | Meeting date (e.g., `YYYY-MM-DD`). |
| `start_time` | string | No | Start time (e.g., `HH:MM`). |
| `end_time` | string | No | End time (e.g., `HH:MM`). |
| `timezone` | string | No | IANA timezone (e.g., `Europe/Berlin`). |
| `location` | string | No | Location or link (Zoom/Teams/Room). |
| `facilitator` | string | No | Meeting facilitator. |
| `note_taker` | string | No | Person taking notes. |
| `attendees` | array&lt;object&gt; | No | List of attendees. See `attendees[]` below. |
| `agenda` | array&lt;string&gt; | No | Agenda topics. |

#### `meeting_meta.attendees[]`
| Name | Type | Required | Description |
|---|---|---|---|
| `name` | string | No | Person’s name. |
| `role` | string | No | Role or function. |
| `email` | string | No | Email (used for context and optional redaction). |

### `controls`
| Name | Type | Required | Description |
|---|---|---|---|
| `output_language` | string | No | Target output language (e.g., `English`). Auto‑detect if omitted. |
| `template` | enum | No | Layout preset: `strict` \| `pm` \| `exec` \| `brief`. Default `strict`. |
| `sections` | array&lt;string&gt; | No | Enable/limit sections to include (e.g., `Summary`, `Decisions`, `Blockers`, `Risks`, `Changes`, `Action Items`, `Discussion Notes`, `Agenda`). |
| `tone` | enum | No | `neutral` \| `concise` \| `detailed`. Default `neutral`. |
| `max_length` | integer | No | Soft cap for total output characters. |
| `redact_pii` | boolean | No | If `true`, masks emails/phones/URLs in output (local regex). |
| `normalize_dates` | boolean | No | Convert deadlines/dates to ISO‑8601; uses provided TZ when present. |
| `glossary` | string or array&lt;string&gt; | No | Domain terms/acronyms to preserve spellings. |
| `project_context` | string or array&lt;string&gt; | No | Context terms; treated like `glossary`. |
| `bullets_style` | enum | No | List bullets: `dash` \| `numbered` \| `checkbox`. Default `dash`. |
| `action_items_format` | string | No | Column order for action items table (e.g., `Task|Owner|Deadline|Priority|Status`). |


### Request Body
```json
{
  "raw_notes": "string, required — plain text or markdown; 20–60k chars sync limit",
  "meeting_meta": {
    "title": "string",
    "date": "YYYY-MM-DD",
    "timezone": "Europe/Berlin",
    "facilitator": "string",
    "note_taker": "string",
    "location": "string",
    "attendees": [{"name": "string", "role": "string", "email": "string"}],
    "agenda": ["string"]
  },
  "controls": {
    "output_language": "English",
    "template": "strict | pm | exec | brief",
    "tone": "neutral | concise | detailed",
    "redact_pii": true,
    "normalize_dates": true,
    "bullets_style": "dash | numbered | checkbox",
    "action_items_format": "Task|Owner|Deadline|Priority|Status"
  }
}
```

### Example Request
```bash
curl -X POST "https://&lt;your-rapidapi-host&gt;/generate.php" \
  -H "Content-Type: application/json" \
  -H "X-RapidAPI-Proxy-Secret: &lt;your-proxy-secret&gt;" \
  -d '{
    "raw_notes": "Project Phoenix meeting: John and Ivan discussed API finalization.",
    "controls": {"output_language": "English", "template": "pm", "tone": "concise"}
  }'
```

### Example Response
```json
{
  "ok": true,
  "data": {
    "minutes": {
      "version": "1.0",
      "confidence": 0.82,
      "meeting": {
        "title": "Project Phoenix meeting",
        "date": "2025-10-19",
        "facilitator": "John",
        "note_taker": "Ivan",
        "attendees": [{"name": "John"}, {"name": "Ivan"}],
        "agenda": []
      },
      "summary": ["API routes finalized."],
      "decisions": ["Merge by Monday."],
      "action_items": [{"task": "Merge API branch", "owner": "", "deadline": "Monday"}]
    },
    "markdown": "# Project Phoenix meeting\n- Attendees: John, Ivan\n..."
  }
}
```

---

## 🧠 2. POST /template-preview.php — Preview Template

### Description
Preview how selected **templates, sections, tone, and formatting controls** will render as **Markdown** before generating full minutes. Returns a Markdown skeleton only (no factual data).

### Headers
```http
Content-Type: application/json
```

### Body (top-level)
| Name | Type | Required | Description |
|---|---|---|---|
| `meeting_meta` | object | No | Optional sample metadata to reflect in the skeleton. |
| `controls` | object | No | Controls that affect layout/sections/style. |
| `sample_notes` | string | No | Optional short notes to influence placeholders (truncated ~20k chars). |

### `meeting_meta`
| Name | Type | Required | Description |
|---|---|---|---|
| `title` | string | No | Example meeting title. |
| `date` | string | No | Example date (`YYYY-MM-DD`). |
| `timezone` | string | No | IANA timezone. |
| `facilitator` | string | No | Example facilitator. |
| `note_taker` | string | No | Example note taker. |
| `location` | string | No | Example location/link. |

### `controls`
| Name | Type | Required | Description |
|---|---|---|---|
| `output_language` | string | No | Target language of the skeleton (defaults to auto). |
| `template` | enum | No | `strict` \| `pm` \| `exec` \| `brief`. |
| `sections` | array&lt;string&gt; | No | Sections to include in the preview (e.g., `Agenda`, `Decisions`, `Action Items`, etc.). |
| `tone` | enum | No | `neutral` \| `concise` \| `detailed`. |
| `bullets_style` | enum | No | `dash` \| `numbered` \| `checkbox`. |
| `action_items_format` | string | No | Column order for action items table. |

### Response (shape)
| Name | Type | Description |
|---|---|---|
| `preview_markdown` | string | Markdown skeleton reflecting the chosen controls; clients will parse JSON and render line breaks. |


### Request Body
```json
{
  "meeting_meta": {"title": "string", "date": "YYYY-MM-DD", "timezone": "Europe/Berlin"},
  "controls": {
    "output_language": "English",
    "template": "strict | pm | exec | brief",
    "tone": "neutral | concise | detailed",
    "bullets_style": "dash | numbered | checkbox",
    "sections": ["Agenda", "Decisions", "Action Items"]
  },
  "sample_notes": "string (optional, short; for flavor)"
}
```

### Example Request
```bash
curl -X POST "https://&lt;your-rapidapi-host&gt;/template-preview.php" \
  -H "Content-Type: application/json" \
  -H "X-RapidAPI-Proxy-Secret: &lt;your-proxy-secret&gt;" \
  -d '{
    "meeting_meta": {"title": "Sprint Planning 43", "date": "2025-10-20"},
    "controls": {"template": "strict", "tone": "neutral", "sections": ["Agenda", "Decisions", "Action Items"]}
  }'
```

### Example Response
```json
{
  "ok": true,
  "data": {
    "preview_markdown": "# Sprint Planning 43\n- Date: 2025-10-20\n- Time: [HH:MM–HH:MM]\n## Agenda\n- [Agenda item placeholder]\n## Decisions\n- [Decision statement placeholder]\n## Action Items\n- Task | Owner | Deadline | Priority | Status\n- [Describe task] | [Owner] | [Date] | [Priority] | [Status]"
  }
}
```

---

## 🔒 3. POST /redact.php — Redact PII Data

### Description
Run **local, deterministic PII masking** on raw notes. Masks emails, phone numbers, and URLs. No AI call, no data storage — ideal for compliance or pre-processing before sending content to `/generate.php`.

### Headers
```http
Content-Type: application/json
```

### Body (top-level)
| Name | Type | Required | Description |
|---|---|---|---|
| `raw_notes` | string | **Yes** | Raw notes to redact; ~20–60k chars. Supports plain text or Markdown. |

### Redaction behavior (placeholders)
| Placeholder | Meaning |
|---|---|
| `[redacted-email]` (masked) | Email addresses are masked (local part partially obfuscated, domain replaced). |
| `[redacted-phone]` | Phone numbers are replaced. |
| `[redacted-url]` | HTTP/HTTPS URLs are replaced. |

### Response (shape)
| Name | Type | Description |
|---|---|---|
| `redacted_notes` | string | The input text with PII placeholders applied. |


### Request Body
```json
{
  "raw_notes": "string, required — plain text or markdown (~20–60k chars)"
}
```

### Example Request
```bash
curl -X POST "https://&lt;your-rapidapi-host&gt;/redact.php" \
  -H "Content-Type: application/json" \
  -H "X-RapidAPI-Proxy-Secret: &lt;your-proxy-secret&gt;" \
  -d '{
    "raw_notes": "Contact: jane.doe@company.com, phone +1-202-555-0100, https://example.com"
  }'
```

### Example Response
```json
{
  "ok": true,
  "data": {
    "redacted_notes": "Contact: j***e@[redacted-domain], phone [redacted-phone], [redacted-url]"
  }
}
```

---

## ⚙️ Controls Reference

| Control | Description |
|----------|--------------|
| `output_language` | Output language for final text (auto-detect if missing). |
| `template` | Layout preset: `strict`, `pm`, `exec`, or `brief`. |
| `tone` | Level of verbosity: `neutral`, `concise`, or `detailed`. |
| `redact_pii` | Removes PII from output automatically. |
| `normalize_dates` | Converts all dates/deadlines to ISO 8601. |
| `bullets_style` | Visual style of bullets: `dash`, `numbered`, or `checkbox`. |
| `action_items_format` | Order of columns for task table. |

---

## 🔐 Privacy & Security
- **No data stored:** Every request is processed in-memory and then discarded.  
- **No content logging:** Meeting content is not saved or reused.  
- **PII protection:** Local regex redaction or optional AI-aware redaction.  
- **HTTPS encryption:** All communications are secured end-to-end.  
- **Compliant:** Suitable for GDPR-safe internal deployments.

---

## 🧠 Summary
- Generate AI meeting minutes with `/generate.php`  
- Preview templates with `/template-preview.php`  
- Redact sensitive content with `/redact.php`

### Key Advantages
✅ Trained on billions of structured meeting samples  
✅ Multilingual and tone-flexible  
✅ Enterprise-grade privacy  
✅ No data storage or content reuse  
✅ Perfect for automation, SaaS, or enterprise integrations  

---

© AI Meeting Minutes Suite. All rights reserved.


© AI Meeting Minutes Suite. All Rights Reserved.

