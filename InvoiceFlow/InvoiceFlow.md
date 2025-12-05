# InvoiceFlow

## Overview
InvoiceFlow is an AI-assisted automation workflow built in n8n that processes incoming invoice files from Google Drive, extracts key information using an AI model, updates a database sheet, and automatically generates an email to the billing team with the extracted details.

This automation eliminates manual data entry, reduces human error, and ensures that invoices are processed quickly and consistently.

---

## Workflow Structure

InvoiceFlow is divided into **three major stages**, shown in the diagram above:

1. **Retrieving invoice from a Google Drive folder**
2. **Extracting and structuring important invoice details**
3. **Generating and sending an email to the billing team**

---

## Tools Used
- **n8n** for workflow automation
- **Google Drive Trigger** to detect new invoice files
- **Extract From File (PDF Extractor)** for extracting raw text from invoices
- **OpenRouter / LLM Model** to interpret invoice text and extract structured fields
- **Google Sheets** to store parsed invoice data
- **n8n Email Node (Gmail)** for sending the invoice summary

---

## How It Works

### **Stage 1: Retrieving Invoice From Drive**
1. **Google Drive Trigger**  
   Fires when a new file is added to a specified "Invoices" folder.

2. **Download Binary**  
   Downloads the actual PDF file so it can be processed.

3. **Extract from File**  
   Uses n8n’s PDF text extraction to convert the invoice document into raw text.

This prepares the invoice for AI extraction.

---

### **Stage 2: Extracting Invoice Information**
4. **Information Extractor (AI Model)**  
   The raw text is passed to an AI model (OpenRouter Chat Model) with a prompt such as:  
   *"Extract invoice number, vendor name, invoice date, amount, due date, and line items from the text below."*

   The model returns structured JSON.

5. **Update DB (Google Sheets)**  
   The parsed invoice fields are appended as a new row in a Google Sheets document.  
   This creates a searchable, permanent invoice log.

---

### **Stage 3: Generating Email for Billing Team**
6. **Create Email (Dynamically Composed Message)**  
   An email body is generated using the structured invoice fields (amount, vendor, invoice number, etc.).

7. **Edit Fields (Formatting Step)**  
   A manual formatter node is used to clean or enrich values (optional).

8. **Send Message (Gmail Node)**  
   Sends the formatted invoice summary to the billing team.  
   The email typically includes:
   - Vendor name  
   - Invoice number  
   - Amount  
   - Due date  
   - Link to the original file in Google Drive  
   - Any special notes extracted by the AI  

---

## Time Savings
InvoiceFlow automates:
- Manual invoice reading  
- Extracting important details  
- Entering data into spreadsheets  
- Writing and sending status emails  

This saves the billing team **hours per week**, reduces errors, and makes invoice processing consistent.

---

## Required Authentications
- **Google Drive API** — for detecting new invoices and downloading files  
- **Google Sheets API** — for logging invoice details  
- **OpenRouter / LLM API Key** — for structured data extraction  
- **Gmail API** — for sending summary emails  


