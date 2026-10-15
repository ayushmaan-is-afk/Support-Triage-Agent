# Support-Triage-Agent

# AI-Powered Email Triage & Escalation Agent

An automated email triage system built with **Activepieces** that classifies incoming support emails, identifies the relevant department, prioritizes high-value client communications, escalates issues to the appropriate authority, and drafts personalized responses ready to send with a single click.

## Overview

Support teams receive emails covering everything from billing disputes and false invoices to technical issues and general inquiries. Manually sorting these emails, identifying the right department, and deciding which issues require immediate attention can slow down response times and cause important client communications to be overlooked.

This workflow automates that process by combining client information, employee records, department-based routing, priority escalation, Slack notifications, and AI-generated response drafts.

Its primary objective is to ensure that **the right issue reaches the right person at the right priority, with a response ready to go.**

## Key Features

- **Automated Email Triggering:** Starts whenever a new email arrives in the designated support inbox.
- **Client and Employee Lookup:** Uses two reference sheets — one containing high-value client information and another containing employee information.
- **Automatic Ticket Management:** Creates a dedicated tickets sheet if one does not already exist.
- **Department Classification:** Determines which department should handle an issue based on the email's content. For example, a false billing claim is routed to Finance.
- **Authority-Based Escalation:** High-value client issues are escalated to the highest-authority employee in the relevant department.
- **Slack Notifications and Flags:** Sends relevant priority and escalation information to Slack so the team can quickly identify important tickets.
- **Personalized Response Drafting:** Generates a contextual response draft tailored to the incoming email.
- **One-Click Response Sending:** Allows the user to send the prepared response with a single click.
- **Limited Draft Regeneration:** Allows the user to rewrite the generated draft up to two times before sending.

## How It Works

### 1. Incoming Email Detection

Activepieces triggers the workflow whenever a new email arrives in the designated support inbox. The email becomes the starting point for the triage process.

### 2. Reference Data Retrieval

The workflow accesses two Google Sheets:

- **High-Value Client Sheet:** Contains information used to identify clients requiring priority handling.
- **Employee Information Sheet:** Contains employee details used to determine departmental ownership and escalation authority.

The workflow also checks whether a dedicated tickets sheet exists and creates it if necessary.

### 3. Email Analysis and Department Classification

The incoming email is analyzed to determine the nature of the request or complaint and identify the appropriate department.

Examples:

| Email Issue | Department |
|---|---|
| False bill or incorrect invoice | Finance |
| Payment or billing dispute | Finance |
| Technical problem | Technical Support |
| Account-related issue | Relevant account-handling department |

These are illustrative examples; actual routing depends on the workflow's classification logic and available department information.

### 4. Client Identification and Priority Assessment

The workflow checks the sender against the high-value client records.

The result determines the escalation path:

- **High-value client:** The ticket receives priority treatment and is routed to the highest-authority employee in the relevant department.
- **Other clients:** The ticket follows the standard handling path defined by the workflow.

This allows the system to account for both the nature of an issue and the importance of the client reporting it.

### 5. Department-Based Escalation

Once the department is identified, the workflow uses employee information to determine the appropriate recipient.

For example, a false-billing complaint from a high-value client is routed to the highest-authority employee in Finance rather than being left for general support handling.

The goal is to reduce manual forwarding and ensure important issues reach someone empowered to resolve them.

### 6. Ticket Logging

The workflow records the relevant email and triage information in the dedicated tickets Google Sheet, providing a structured place to track incoming issues and their priority.

The sheet is created automatically if it does not already exist.

### 7. Slack Notifications

The workflow sends relevant flags and escalation details to Slack.

High-value client issues are marked **HIGH PRIORITY**, making it easier for the team to identify urgent communications and direct attention to the right tickets.

### 8. AI-Generated Response Draft

The workflow generates a personalized response draft using the context of the incoming email.

The user can:

1. Review the generated draft.
2. Send it with a single click.
3. Request a rewrite if the response needs improvement.
4. Regenerate the draft up to two times.

This keeps a human in control of the final communication while reducing the time required to write routine support responses.\

## Technology Stack

| Component | Purpose |
|---|---|
| Activepieces | Workflow orchestration and automation |
| Email integration | Detects new support emails and supports response sending |
| Google Sheets | Stores client records, employee information, and tickets |
| Slack | Communicates priority flags and escalation details |
| AI / LLM integration | Supports email classification and personalized response drafting |

## Expected Benefits

- **Faster triage:** Reduces manual email sorting and departmental assignment.
- **Improved escalation:** Directs high-value client issues to the appropriate departmental authority.
- **Better visibility:** Centralizes ticket records and communicates priority flags through Slack.
- **Reduced response time:** Provides a personalized response draft without requiring the team to start from scratch.
- **Human-controlled communication:** Keeps the final send decision with the user.
- **Consistent handling:** Applies a structured process to incoming support requests.

## Design Philosophy

The workflow combines **automated classification, business-aware prioritization, authority-based routing, and human-approved communication**.
Rather than treating every incoming email equally, it considers who is contacting the company, what the issue concerns, which department owns it, and whether escalation is required.
The result is a support workflow designed to help teams handle important client issues more efficiently without removing human oversight from customer communication.

## REQUIREMENTS - 
1. Activepieces
2. Two populated google sheets named - Employee Information, Client Information respectively. 

Flow Diagram - 
<img width="5344" height="8192" alt="V2 triage" src="https://github.com/user-attachments/assets/e9517f8d-d827-40f6-9de4-54069c527670" />


