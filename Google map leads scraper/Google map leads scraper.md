# Google Maps Leads Scraper

## Overview
Google Maps Leads Scraper is an automation workflow designed to extract business leads from Google Maps based on a specific location and keyword. It uses Apify for scraping business data, n8n to orchestrate the workflow, and Google Sheets to store and filter the final leads.

The system automatically removes closed or inactive businesses, ensuring that only high-quality leads are saved.

## Tools Used
- **n8n**: Controls the workflow from input to storage.
- **Apify**: Uses the Google Maps Scraper actor to collect business data.
- **Google Sheets**: Stores the final list of leads after filtering.
- **Iterator Node**: Used to process each scraped business individually.

---

## How It Works

### **1. Input Parameters**
The workflow starts with:
- A **location** (e.g., “Lagos”, “New York”)
- A **keyword** (e.g., “plumber”, “restaurant”, “dentist”)

These parameters are sent into the automation manually or from a form.

---

### **2. Apify Google Maps Scraper**
n8n triggers the **Apify Google Maps Scraper** Actor.

Apify returns a full list of businesses containing:
- Business name  
- Address  
- Website  
- Phone number  
- Rating  
- Total reviews  
- Opening status (open/closed)  
- Google Maps URL  
- Coordinates  
- Categories  

---

### **3. Iterate Through Results**
n8n’s **Item Lists → Split/Iterator Node** processes each returned result one-by-one.

This step allows filtering and evaluating each business individually.

---

### **4. Filter Closed Businesses**
A **Router** or **IF node** checks:
IF business.status == "CLOSED" discard it ELSE send to Google Sheets
Only open/active businesses are allowed through.

This ensures you never store:
- Closed stores  
- Permanently shut-down locations  
- Invalid leads  

---

### **5. Store Leads in Google Sheets**
Each valid business is inserted into a Google Sheets file with fields like:
- Business Name  
- Category  
- Address  
- Phone  
- Website  
- Rating  
- Reviews  
- Google Maps URL  
- Latitude / Longitude  
- Timestamp  

This results in a clean, ready-to-use lead list.

---

## Time Savings
This workflow replaces hours of:
- Manually searching Google Maps  
- Copying and pasting business info  
- Filtering out closed/unverified businesses  
- Organizing everything into a spreadsheet  

It can generate **hundreds of clean leads** in minutes.

---

## Required Authentications
- **Apify API Token**: To run the Google Maps Scraper Actor.
- **Google Sheets API**: To insert lead data into your sheet.
- **n8n Credentials**: For orchestrating the automation.

---

## Future Improvements
- Add email/phone verification using external APIs.
- Automatically enrich leads with domain info (e.g., Clearbit).
- Add a scheduler to scrape new leads weekly or monthly.
- Send the lead sheet link automatically to WhatsApp or email.
