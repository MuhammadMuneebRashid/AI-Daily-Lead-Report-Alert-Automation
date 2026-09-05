# 🤖 AI Lead Analysis & Automated Reporting System

An AI-powered **n8n automation workflow** that automatically collects leads from Google Sheets, filters already-processed records, analyzes leads using **Google Gemini**, separates them into **problematic and normal leads**, generates a combined report, sends the report via Gmail, and marks the processed leads as **Sent**.

This workflow is designed to reduce manual lead analysis and provide teams with a consistent automated lead-reporting process.

---

## 🚀 Features

* ⏰ **Scheduled Automation**

  * Runs automatically using an n8n Schedule Trigger.

* 📊 **Google Sheets Integration**

  * Reads lead information directly from a Google Sheet.
  * Uses the lead's `report_status` to identify unprocessed records.

* 🔍 **Lead Filtering**

  * Automatically ignores leads that have already been marked as `sent`.
  * Processes only new/unreported leads.

* 🧠 **AI-Powered Lead Analysis**

  * Uses **Google Gemini Flash** through the n8n AI Agent.
  * Analyzes all collected leads together instead of generating individual reports.

* 🚨 **Problematic Lead Detection**

  * Separates leads into:

    * Problematic Leads
    * Normal Leads

* 📋 **Combined Reporting**

  * Generates a consolidated report for the processed leads.
  * Creates a separate alert message for problematic leads.

* 📧 **Automated Email Reporting**

  * Sends the generated report through Gmail.

* ✅ **Automatic Status Updates**

  * After the report is sent, processed rows are updated with:
    `report_status = sent`

---

## 🔄 Workflow

```text
Schedule Trigger
       ↓
Get Leads from Google Sheets
       ↓
Filter Unprocessed Leads
       ↓
Prepare Lead Data
       ↓
AI Agent + Google Gemini
       ↓
Analyze & Categorize Leads
       ↓
Generate Structured Report
       ↓
Send Report via Gmail
       ↓
Identify Processed Rows
       ↓
Update Google Sheets
       ↓
Mark Leads as "Sent"
```

---

## 🧩 Workflow Components

### 1. Schedule Trigger

The workflow starts automatically through an n8n Schedule Trigger.

The current workflow is configured with a scheduled execution time.

### 2. Get Rows from Google Sheets

The workflow retrieves lead records from Google Sheets.

The sheet contains information such as:

* Name
* Email
* Company Name
* Company Size
* Country
* Industry
* Estimated Budget
* Project Description
* Service Required
* Report Status
* Row Number

---

### 3. JavaScript Lead Processing

A JavaScript Code node filters the incoming records.

Only leads whose `report_status` is **not `sent`** are processed.

The workflow then prepares the lead information into a structured text format before sending it to the AI Agent.

---

### 4. AI Lead Analysis

The AI Agent receives the collected lead data and analyzes the leads as a group.

The AI is instructed to:

* Analyze all leads
* Separate problematic and normal leads
* Create a combined report
* Provide processed row numbers
* Generate an alert message for problematic leads

This prevents the workflow from sending a separate email for every individual lead.

---

### 5. Google Gemini

The workflow uses **Google Gemini Flash** as the AI language model for lead analysis.

---

### 6. Structured AI Output

A Structured Output Parser ensures that the AI response follows a predictable JSON structure.

Expected output includes:

```json
{
  "status": "",
  "problematic_leads": "",
  "normal_leads": "",
  "report": "",
  "alert_message": "",
  "processed_rows": ""
}
```

This makes the AI response easier to process in the following automation steps.

---

### 7. Gmail Report

After analysis, the generated report is sent automatically through Gmail.

The email uses the AI-generated `report` as the message content.

---

### 8. Update Processed Leads

After the email is successfully sent, the workflow identifies the rows that were processed and updates their status.

```text
report_status → sent
```

The row number is used as the matching field when updating the Google Sheet.

This prevents the same leads from being included in future reports.

---

## 📌 Lead Processing Logic

The workflow follows this logic:

```text
IF report_status = "sent"
        ↓
    Skip Lead

IF report_status != "sent"
        ↓
    Process Lead
        ↓
    Send Report
        ↓
    Mark as "sent"
```

This provides a simple mechanism for avoiding duplicate reporting.

---

## 🛠️ Technologies Used

| Technology                   | Purpose                        |
| ---------------------------- | ------------------------------ |
| **n8n**                      | Workflow automation            |
| **Google Sheets**            | Lead data storage              |
| **JavaScript**               | Data filtering and preparation |
| **Google Gemini**            | AI-powered lead analysis       |
| **Gmail**                    | Automated report delivery      |
| **Structured Output Parser** | Consistent AI response format  |

---

## ⚙️ Setup

### Prerequisites

Before importing the workflow, make sure you have:

* n8n installed or hosted
* Google Sheets access
* Google Gemini credentials
* Gmail credentials
* A Google Sheet containing your lead data

### Google Sheets

Create a sheet containing the required lead fields, including:

```text
name
email
company_name
company_size
country
industry
estimated_budget
service_required
project_description
report_status
row_number
```

### n8n Credentials

Configure the required credentials for:

* Google Sheets
* Gmail
* Google Gemini

Then import the workflow JSON into n8n.

---

## 📊 Example Use Case

A sales team collects leads through a form and stores them in Google Sheets.

Instead of manually reviewing every lead:

1. The workflow runs automatically.
2. New leads are collected.
3. Previously reported leads are ignored.
4. Gemini analyzes the new leads.
5. Leads are categorized as normal or problematic.
6. A consolidated report is generated.
7. The report is emailed to the team.
8. Processed leads are marked as `sent`.

This allows the sales team to focus on important leads instead of manually reviewing spreadsheets.

---

## 🔐 Security

When publishing this workflow to GitHub:

* **Do not expose API keys or passwords.**
* Remove or replace credential IDs.
* Avoid publishing private Google Sheet IDs.
* Avoid exposing personal email addresses.
* Configure credentials directly inside your n8n instance.

---

## 📈 Benefits

* Reduces manual lead analysis
* Automates recurring reporting
* Prevents duplicate reports
* Uses AI for lead classification
* Centralizes lead analysis
* Provides automated team notifications
* Saves time for sales and operations teams

---

## 🔮 Future Improvements

Possible improvements include:

* Add Slack or Microsoft Teams notifications
* Create lead priority scores
* Automatically assign leads to sales representatives
* Add CRM integration
* Generate daily/weekly/monthly analytics
* Store AI analysis history
* Add dashboards for lead performance
* Send separate alerts for high-priority leads

---

## 👨‍💻 Project Type

**AI Automation | Lead Management | n8n Workflow | AI-Powered Reporting**

---

## 📄 License

This project is available for learning, development, and personal automation purposes. Add an appropriate open-source license if you plan to distribute or modify it publicly.



<img width="1920" height="1080" alt="report 2" src="https://github.com/user-attachments/assets/2cc41c02-de43-42f7-b5d5-c533de33bcf0" />

<img width="1920" height="1080" alt="project 36" src="https://github.com/user-attachments/assets/1bf94b17-c856-4263-aff9-f8d1fa10cb96" />


