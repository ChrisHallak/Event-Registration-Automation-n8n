# Arab Automators Event Registration Automation

A simple n8n workflow for automating the registration process for the Arab Automators event.

The workflow collects the attendee's information through a Tally form, saves the registration data, and optionally sends an acceptance email based on the attendee's preference.

## How It Works

The workflow follows this process:

Tally Form
   ↓
Insert Registration
   ↓
Edit Fields
   ↓
Check Email Preference
   ↓
Send Acceptance Email (if requested)

### 1. Tally Form

The attendee fills out a form with:

- Name
- Email
- Event attendance date
- Whether they want to receive an acceptance email

### 2. Store Registration

After submitting the form, the registration data is saved for record keeping.

### 3. Process the Data

The workflow prepares the submitted fields before checking the attendee's email preference.

### 4. Check Email Preference

An `IF` node checks whether the attendee requested an acceptance email.

- If `true` → send an email
- If `false` → finish the workflow without sending an email

### 5. Send Acceptance Email

If the attendee selected the acceptance-email option, Gmail sends an acceptance message to the email address provided in the form.

## Workflow

The main workflow consists of:

- **Tally Trigger** — receives new form submissions
- **Insert Row** — stores the registration
- **Edit Fields** — prepares the required data
- **IF** — checks the email preference
- **Gmail** — sends the acceptance email

## Technologies

- [n8n](https://n8n.io/)
- [Tally](https://tally.so/)
- Google Sheets
- Gmail

## Use Cases

This workflow can be adapted for:

- Event registration
- Conference attendance
- Workshop registration
- Meetup registration
- Webinar registration
- Community events

The same structure can also be extended to include confirmation emails, reminders, attendance tracking, or notifications.

## Setup

### 1. Create the Tally Form

Create a Tally form containing the required fields:

- Name
- Email
- Date
- Acceptance email preference

### 2. Connect Tally to n8n

Create a Tally Trigger node and connect it to your form.

### 3. Configure the Storage

Connect the `Insert Row` node to your Google Sheet or preferred storage system.

Make sure the required columns match the fields coming from Tally.

### 4. Configure the IF Node

Set the condition to check the attendee's email preference.

For example:

```text
Email Acceptance = true
