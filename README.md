# Project 3 – GHL Client Onboarding Automation

## Overview
An automated client onboarding workflow built using self-hosted n8n, Google Sheets, and Gmail.

This project demonstrates how client information can be captured, recorded, and processed automatically, reducing manual onboarding work.

**Implementation note:** This is an n8n-based alternative to the originally proposed GoHighLevel/Zapier workflow. It does not include a live GoHighLevel integration.

## Features
- Receive new client information through a POST webhook
- Automatically create client records in Google Sheets
- Send personalized welcome emails using Gmail
- Create onboarding tasks with assigned team, status, and due date
- Retry failed Google Sheets and Gmail operations

## Technology Stack
- n8n (self-hosted using Docker)
- Google Sheets
- Gmail
- Webhook API
- PowerShell (for local testing)

## Workflow Architecture

Webhook → Google Sheets (Client Record) → Gmail (Welcome Email) → Google Sheets (Onboarding Task)

## Screenshots

### Successful Workflow Execution
![Successful Workflow](Screenshot%202026-11-14%20225859.png)

### Client Records in Google Sheets
![Client Records](Image%20Nov%2014%2C%202026%2C%2010_56_48%20PM.png)

### Onboarding Task Records
![Onboarding Tasks](Image%20Nov%2014%2C%202026%2C%2010_52_22%20PM.png)

## Setup Instructions

1. Install Docker Desktop and run a self-hosted n8n instance.
2. Import the exported workflow JSON into n8n.
3. Configure Google Sheets OAuth2 and Gmail OAuth2 credentials.
4. Create a Google spreadsheet with two tabs.

**Sheet1 – Client Records**

Client Name, Client Email, Company Name, Phone, Service, Status

**Sheet2 – Onboarding Tasks**

Client Name, Client Email, Task Name, Assigned To, Status, Due Date

5. Select the correct spreadsheet and tabs in both Google Sheets nodes.
6. Save the workflow and start listening for a test webhook.

## Testing

Send a POST request to the local test webhook:

`http://localhost:5678/webhook-test/client-onboarding`

Example JSON payload:

```json
{
  "client_name": "John Smith",
  "client_email": "your-test-email@example.com",
  "company_name": "Smith Digital Agency",
  "phone": "+15551234567",
  "service": "AI Automation"
}
```

Replace the example email with an email address you control before testing.

### Verified Results
- Webhook successfully received test client data
- Client records were added to Google Sheets
- Welcome email node executed successfully
- Onboarding task was created
- All four workflow nodes completed successfully in the recorded test

## Error Handling
Retry-on-failure settings are enabled on the Google Sheets and Gmail nodes, with a two-second wait between attempts.

A separate error notification workflow is not implemented.

## Limitations
- Direct GoHighLevel integration is not implemented.
- The webhook is hosted locally and is not publicly accessible without additional deployment or tunneling.
- The workflow creates one initial onboarding task per request.
- OAuth credentials must be configured separately after importing the workflow.
- A Loom demonstration video is not included in this submission.

## Repository Contents
- Exported n8n workflow JSON
- README documentation
- Workflow execution screenshot
- Client records screenshot
- Onboarding tasks screenshot

## Project Status
Core n8n alternative workflow implemented and successfully tested with sample data.

**Project:** Think AI Works – Internship Project 3
