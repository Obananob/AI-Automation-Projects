# YouTube Comment Scraper

## Overview
YouTube Comment Scraper is an automation workflow built using n8n, Apify, and Airtable.  
Its purpose is to extract comments from a specific YouTube video, store the results in Airtable, and keep them organized for analysis, marketing insights, or sentiment tracking.

This automation eliminates the need for manual scraping and ensures comments are stored cleanly and consistently.

## Tools Used
- **n8n**: Orchestrates the workflow.
- **Apify YouTube Scraper**: Extracts comments from YouTube videos.
- **Airtable**: Stores scraped comments in a structured table.

## How It Works
1. **Input Video URL**
   - The user submits the URL of the YouTube video they want to scrape.

2. **Call Apify Actor**
   - n8n sends a request to Apify’s YouTube Comment Scraper actor with the video URL.
   - Apify scrapes all available comments, usernames, timestamps, etc.

3. **Iterator Node in n8n**
   - n8n receives the full dataset and splits it into individual comment items for processing.

4. **Airtable Entry Creation**
   - Each comment is added to an Airtable table.
   - Stored fields typically include:
     - Comment text  
     - Username  
     - Comment ID
     - Page URL

5. **Completion**
   - Once all comments are inserted into Airtable, the workflow ends.
   - Airtable now contains a clean, structured list of all comments for future use.

## Time Savings
This automation eliminates:
- Manual comment collection  
- Copy-paste work  
- Disorganized data  

It is especially useful for:
- Content creators  
- Marketing teams  
- Researchers  
- Customer sentiment analysis  

## Required Authentications
- **Apify API Token**: To run the YouTube scraper.
- **Airtable API Key**: To store comments in a table.

## Future Improvements
- Add sentiment analysis using OpenAI to classify comments.
