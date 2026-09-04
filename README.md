# AI Daily Lead Report & Alert Automation

## 📌 Project Overview

This project is an AI-powered lead processing and daily reporting automation built with n8n.

The system collects lead information from a Tally Form, stores it in Google Sheets, and then automatically analyzes the leads using Gemini AI.

The AI identifies whether a lead is *Normal* or *Problematic*.

- Problematic leads → Alert is sent to the Team and Owner
- Normal leads → Daily report is sent to the Owner

---

## 🔄 Workflow

### Workflow 1 – Lead Collection

Tally Form
↓
Webhook
↓
Edit Fields
↓
Google Sheets (Append Row)


### Workflow 2 – Daily Lead Analysis

Schedule Trigger
↓
Google Sheets (Get Rows)
↓
AI Agent (Gemini)
↓
Structured Output
↓
IF
↙️        ↘️
Problem   Normal
↓           ↓
Alert      Report
↓           ↓
Team +     Owner
Owner

---

## ⚙️ How It Works

1. A user submits their information through the Tally Form.
2. The Webhook receives the submitted data.
3. Edit Fields prepares the data in the required format.
4. The lead is stored in Google Sheets.
5. The Schedule Trigger starts the daily reporting workflow.
6. Google Sheets retrieves the stored lead data.
7. Gemini AI analyzes the leads.
8. Structured Output validates the AI response in JSON format.
9. The IF node checks whether the lead is problematic or normal.
10. If the lead is problematic, an alert email is sent to the Team and Owner.
11. If the lead is normal, a daily report is sent to the Owner.

---

## 🤖 AI Classification

The AI classifies leads into two categories:

### Problem
The lead requires attention or action.

### Normal
The lead does not require immediate attention.

---

## 🛠️ Technologies Used

- n8n
- Tally Forms
- Webhooks
- Google Sheets
- Gemini AI
- AI Agent
- Structured Output
- IF Node
- Email Automation

---

## 🎯 Project Goal

The goal of this automation is to reduce manual lead monitoring and provide the business owner with an automated daily overview of leads while immediately alerting the responsible team when a problematic lead is detected.

---

## 🚧 Project Status

*Work in Progress 🚧*

The project is currently under development and will be continued.

Upcoming work includes:
- Completing the n8n workflow
- Testing lead classification
- Testing email alerts
- Testing daily reports
- Improving AI prompts
- Final workflow testing
- Documentation and demo

---

## 👨‍💻 Built With

*n8n + Gemini AI + Tally Forms + Google Sheets*

## Still in progress
<img width="1920" height="1080" alt="report 2" src="https://github.com/user-attachments/assets/2cc41c02-de43-42f7-b5d5-c533de33bcf0" />

<img width="1920" height="1080" alt="report data" src="https://github.com/user-attachments/assets/0d7dec4c-a3a5-4320-ba8e-c53c5c5425fe" />

