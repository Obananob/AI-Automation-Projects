# InvoiceFlow

## Overview
InvoiceFlow is an automation built using n8n that streamlines the handling of incoming invoices. Instead of manually checking emails, downloading attachments, and organizing files, InvoiceFlow automatically detects invoice emails, uploads the invoice file to Google Drive, and notifies the billing team with a link to the stored file.

This automation removes repetitive work, reduces errors, and ensures all invoices are properly stored and tracked.

## Tools Used
- **n8n**: Orchestrates the automation workflow.
- **Gmail Trigger**: Detects new incoming invoice emails.
- **Google Drive**: Stores uploaded invoice documents.
- **Email Notifications (Gmail Node)**: Sends alerts to the billing team.

## How It Works
1. **Email Trigger**
   - The automation starts when a new email arrives in the designated inbox.
   - It filters for invoice-related emails using subject keywords or attachment checks.

2. **Attachment Extraction**
   - InvoiceFlow retrieves the invoice file(s) attached to the email (PDF, image, etc.).

3. **Google Drive Upload**
   - The attached invoice file is uploaded to a specific "Invoices" folder in Google Drive.
   - A unique file name or timestamp may be applied to avoid overwriting existing files.

4. **Team Notification**
   - Once the file is successfully uploaded, n8n sends an email to the billing or finance team.
   - The email includes:
     - Invoice name  
     - Sender  
     - Date received  
     - Direct Google Drive link to the uploaded file  

5. **Record Keeping (Optional)**
   - The workflow can log invoice metadata (sender, timestamp, file URL) in a Google Sheet or database for tracking and auditing.

## Time Savings
InvoiceFlow eliminates repetitive manual tasks:
- No more downloading attachments one by one
- No more manually uploading to Drive
- No need to notify the billing team manually
- Reduces the chance of losing or misplacing an invoice

This automation can save **hours per week** and ensures invoices are processed consistently.

## Required Authentications
- **Gmail API**: For reading incoming emails and sending notifications.
- **Google Drive API**: For uploading invoice documents into Drive.

## Future Improvements
- Automatically extract invoice amounts and vendor names using OCR/AI.
- Add duplicate detection to avoid re-uploading the same invoice.
- Integrate with an accounting system (e.g., QuickBooks, Zoho Books).
