# Customer Feedback & Discount Automation

An n8n workflow that automates customer feedback collection and reward-based discount logic using conditional branching and Google Sheets integration.

## Overview

This workflow captures customer feedback for a product through a web form, evaluates the sentiment, and automatically determines discount eligibility, all data is then logged to Google Sheets for tracking and analysis.

## How It Works

1. **Form Trigger** - Customer submits feedback through a web form with the following fields:
   - Email
   - Name
   - Age
   - Feedback (Positive / Negative / Neutral)

2. **IF Condition** - The workflow checks the feedback value:
   - If feedback is **Positive** → routes to the discount-approval path
   - If feedback is **Negative** or **Neutral** → routes to the no-discount path

3. **Edit Fields (Set) Nodes**
   - **Discount_Yes** - tags the record with `Give-Discount: Yes`
   - **Discount_No** - tags the record with `Give-Discount: No`

4. **Google Sheets** - Both branches merge and append the final record (Email, Name, Age, Feedback, Give-Discount) into a connected Google Sheet.

## Workflow Diagram
Form Trigger → IF (Feedback Check)
├── Positive → Set (Discount: Yes) → Google Sheets
└── Negative/Neutral → Set (Discount: No) → Google Sheets

## Tech Stack

- **n8n** - workflow automation
- **Google Sheets API** - data storage
- **Webhook Form Trigger** - customer input collection

## Use Case

This workflow is a lightweight example of automating a customer loyalty/reward system, useful for small businesses that want to reward positive feedback with discounts while tracking all customer responses in one place, without any manual data entry.

## Setup

1. Import `workflow.json` into your n8n instance.
2. Connect your Google Sheets credentials.
3. Update the Google Sheet ID/tab in the "Append row in sheet" node.
4. Publish the workflow to get your live form URL.

## Author

Built by Mujahid Toorie - Freelance Python Developer & AI Automation Specialist  
