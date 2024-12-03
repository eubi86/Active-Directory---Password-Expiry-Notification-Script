# Active-Directory---Password-Expiry-Notification-Script
Active Directory Password Expiry Notification Script
This PowerShell script automates the process of notifying users and administrators about upcoming Active Directory password expirations. Designed for environments with structured Organizational Units (OUs), it sends email alerts to responsible individuals (based on an extensionAttribute15 value) or the support team when a user's password is about to expire. The script helps organizations proactively manage password expirations and ensure seamless access for users.

Features
Password Expiry Notifications:

Alerts responsible users (email address extracted from extensionAttribute15) when a user's password is set to expire in 14 or 1 day.
Sends reminders to the IT support team if no responsible email address is found.
Customizable Email Notifications:

Emails include user details such as first name, last name, email, UPN, expiration date, and days remaining.
Includes support for HTML-formatted email bodies.
Adds custom headers (e.g., X-Sophos-SPX-Encrypt) for additional processing needs.
Organizational Unit Targeting:

Scans a specified Active Directory Organizational Unit (OU) and its sub-OUs for users.
Filters and processes user accounts with relevant attributes.
Error Handling:

Logs and handles errors when sending emails to ensure reliability.
Prerequisites
PowerShell 5.1 or later
Active Directory PowerShell Module
SMTP server for email notifications
Configuration
Edit the following configuration variables in the script to match your environment:

$OU: Define the target OU in Active Directory (e.g., "OU=Hosting,DC=ad,DC=domain,DC=com").
$EmailSender: Specify the sender email address for notifications.
$SmtpServer, $SmtpPort: Configure SMTP server details.
$SupportEmail: Set the support team's email address for fallback notifications.
Usage
Ensure the script has the necessary permissions to query Active Directory and send emails.
Update the configuration variables to match your environment.
Run the script using PowerShell:
powershell
Code kopieren
.\PasswordExpiryNotification.ps1
Example Email
Responsible Party Notification:
Subject: Password Expiry Notification: User Password Expiring in 14 Days
Body:
User details
Expiry date and days remaining
HTML table for better readability
Support Team Notification:
Subject: Warning: Password Expiry Imminent for Users Without Responsible Email
Body: Detailed list of affected users without assigned responsible parties.
