# Project 3 – GHL Client Onboarding Automation

## Overview
Client onboarding automation built using self-hosted n8n, Google Sheets, and Gmail.

## Workflow
Webhook → Google Sheets (Client Record) → Gmail (Welcome Email) → Google Sheets (Onboarding Task)

## Features
- Receive new client information through a webhook
- Store client details in Google Sheets
- Send automated welcome emails
- Create onboarding tasks with due dates
- Retry failed operations

## Implementation Note
This is an n8n-based alternative implementation. Direct GoHighLevel integration is not included.

## Testing
Tested using sample client data. Client records, welcome emails, and onboarding tasks were successfully generated.
