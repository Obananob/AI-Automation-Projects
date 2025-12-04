# AutoMail

## Overview
AutoMail is an email automation workflow that sends personalized emails to students based on their class. Using n8n and Google Sheets, it ensures each student receives the right message without manual intervention.

## Tools Used
- **n8n**: Manages the entire workflow from form submission to email delivery.
- **Google Sheets**: Used to read student data and store campaign information.

## How It Works
1. **Form Submission**: The admin submits a form that includes the email subject, message body, and a dropdown to select the target class.
2. **Campaign ID Generation**: The workflow generates a unique campaign ID for tracking.
3. **Google Sheets Lookup**: It reads through the Google Sheets to find students in the specified class.
4. **Switch Node for Class Routing**: A switch node directs the workflow based on the selected class (e.g., 100 level, 200 level) to ensure the right recipients.
5. **Email Sending via Gmail Node**: After looping through the selected students, the workflow sends personalized emails using the Gmail node. Each email includes the specified subject and message body from the form submission.
6. **Looping and Completion**: The workflow loops through all students in the class until everyone has received the email.

## Time Savings
AutoMail saves several hours of manual emailing each week, reducing human error and freeing up staff time.

## Required Authentications
- **Google Sheets API**: Needed to read student data and log email activity.
- **Gmail API**: Required for sending emails through the Gmail node.

## Future Improvements
- Add support for multiple notification channels (e.g., SMS).
- Allow customization of email templates for different classes.
