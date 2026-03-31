# Lead-Capture-from-Webhooks-to-Updating-into-CRM-and-Sending-Email-N8N

A simple and effective **n8n lead capture automation workflow** that receives lead data via webhook, creates or updates the contact in **HighLevel CRM**, and automatically sends a follow-up email using **Gmail**. This workflow is ideal for businesses, clinics, agencies, and service providers that want to instantly capture and respond to incoming leads. :contentReference[oaicite:1]{index=1}

---

## Features

- Receives lead data through a **Webhook**
- Captures:
  - Name
  - Email
  - Phone number
- Automatically creates or updates a contact in **HighLevel CRM**
- Sends an automatic acknowledgment email to the lead
- Useful for lead forms, landing pages, chatbot submissions, and external apps
- Lightweight and easy to integrate into existing systems :contentReference[oaicite:2]{index=2}

---

## Workflow Overview

This workflow follows the process below:

1. A lead submits their information through an external form or app
2. The data is sent to an **n8n Webhook**
3. The workflow extracts the lead's:
   - name
   - email
   - phone
4. The lead is then created or updated inside **HighLevel CRM**
5. A follow-up email is sent automatically through **Gmail** to confirm receipt of the inquiry :contentReference[oaicite:3]{index=3}

---

## Nodes Used

### 1. Webhook
The workflow starts with a **Webhook** node.

It listens for incoming **POST requests** and accepts lead data from an external source such as:

- Website form
- Landing page
- Chatbot
- CRM form
- Third-party application
- Custom frontend form :contentReference[oaicite:4]{index=4}

---

### 2. Create or Update Contact (HighLevel)
This node sends the incoming lead data to **HighLevel CRM**.

It maps the following fields:

- **Email** → `body.email`
- **Phone** → `body.phone`
- **Name** → `body.name`

This ensures that:

- new leads are created automatically
- existing contacts are updated if they already exist in the CRM :contentReference[oaicite:5]{index=5}

---

### 3. Send a Message (Gmail)
After the lead is saved in the CRM, the workflow sends a confirmation email using **Gmail**.

The current email message is:

> Hi {{name}}, thanks for reaching out to [Clinic Name]. Our team will get back to you shortly.

This can be customized for any business or use case such as:

- clinics
- agencies
- consultants
- sales teams
- customer support flows :contentReference[oaicite:6]{index=6}

---

## Incoming Webhook Payload Example

This workflow expects a payload similar to the following:

```json
{
  "body": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+1234567890"
  }
}
