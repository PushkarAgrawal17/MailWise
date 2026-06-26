# MailWise

**MailWise** is an AI-powered email assistant built with **n8n**, **Groq**, **Gmail API**, and **Google Calendar API**. It automatically organizes your inbox, labels emails, detects important events, creates calendar entries, generates reply drafts, and cleans up spam—reducing manual email management.

---

## Features

* AI-powered email classification
* Automatic Gmail labeling
* Calendar event extraction and creation
* AI-generated reply drafts (saved as Gmail drafts)
* Spam cleanup with digest notification
* Multi-label support for emails
* Scheduled inbox monitoring

---

## Workflow Overview

When a new unread email is detected, MailWise:

1. Retrieves unread emails from Gmail.
2. Uses an LLM to analyze the email.
3. Generates:

   * Labels
   * Summary
   * Event information
   * Reply requirement
4. Applies Gmail labels automatically.
5. Creates a Google Calendar event if an event is detected.
6. Generates a reply draft if a response is required.
7. Moves spam emails to Trash.
8. Sends a cleanup digest after spam removal.

---

## Tech Stack

- **Automation:** n8n
- **LLM:** Groq
- **Email Integration:** Gmail API
- **Calendar Integration:** Google Calendar API
- **Deployment:** Docker

---

## Project Structure

```
MailWise/
│
├── workflow.json
├── README.md
└── .env.example
```
> Note: MailWise stores credentials securely using n8n's built-in credential manager. The .env.example file is provided only to document the required configuration and is not consumed directly by the workflow.

---

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/MailWise.git
cd MailWise
```

### 2. Import the workflow

Import `workflow.json` into your n8n instance.

### 3. Configure credentials

Create the following credentials inside n8n:

* Gmail OAuth2
* Google Calendar OAuth2
* Groq API

### 4. Create Gmail labels

Create these labels in Gmail:

* Urgent
* College/TnP
* Opportunities
* Bills & Subscriptions
* Informational

Then open each **Add Label** node in n8n and select the corresponding Gmail label.

### 5. Configure the workflow

* Select your Google Calendar in the Calendar node.
* Replace `YOUR_EMAIL@gmail.com` inside the Cleanup Digest node.
* Add your Groq credentials to both AI nodes.
* Enable the workflow.

---

## Example AI Output

```json
{
  "labels": [
    "Urgent",
    "Opportunities"
  ],
  "summary": "TechCorp has scheduled your interview for Monday at 2 PM.",
  "hasEvent": true,
  "replyNeeded": true,
  "eventTitle": "TechCorp Interview",
  "eventDateTime": "2026-06-30T14:00:00"
}
```

---

## Future Improvements

* Daily inbox summary
* Task extraction
* Follow-up reminders
* Job application tracker
* Attachment summarization
* Sender reputation scoring
* AI-powered search

---

## Author

**Pushkar Agrawal**
B.Tech CSE — Jaypee Institute of Information Technology, Noida (2024–2028)

[GitHub](https://github.com/PushkarAgrawal17) · [LinkedIn](https://linkedin.com/in/pushkaragrawal17)
