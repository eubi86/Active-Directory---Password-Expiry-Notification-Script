# Active Directory Password Expiry Notification Script

This PowerShell script automates the process of notifying users and administrators about upcoming Active Directory password expirations. Designed for environments with structured Organizational Units (OUs), it sends email alerts to responsible individuals (based on an `extensionAttribute15` value) or the support team when a user's password is about to expire. The script helps organizations proactively manage password expirations and ensure seamless access for users.

---

## Features

### **Password Expiry Notifications**
- Alerts responsible users (email address extracted from `extensionAttribute15`) when a user's password is set to expire in **14** or **1 day**.
- Sends reminders to the IT support team if no responsible email address is found.

### **Customizable Email Notifications**
- Emails include user details such as:
  - First name
  - Last name
  - Email
  - UPN
  - Expiration date
  - Days remaining until expiration
- Supports **HTML-formatted** email bodies.


### **Organizational Unit Targeting**
- Scans a specified Active Directory **Organizational Unit (OU)** and its sub-OUs for users.
- Filters and processes user accounts with relevant attributes.

### **Error Handling**
- Logs and handles errors when sending emails to ensure reliability.

---

## Prerequisites

- **PowerShell 5.1** or later
- Active Directory PowerShell Module
- SMTP server for email notifications

---

## Configuration

Edit the following configuration variables in the script to match your environment:

### **Active Directory Target OU**
Define the target OU in Active Directory:
```powershell
$OU = "OU=Hosting,DC=ad,DC=domain,DC=com"
```
Email Settings
Sender Email Address: Specify the sender email address for notifications.
```powershell
$EmailSender = "no-reply@yourdomain.com"
```
SMTP Server Configuration: Set the SMTP server details.
```powershell
$SmtpServer = "smtp.yourdomain.com"
$SmtpPort = 587
```
Support Team Email Address: Provide a fallback email address for support.
```powershell
$SupportEmail = "support@yourdomain.com"
```
Query Active Directory.
Send emails via the configured SMTP server.
Update the configuration variables in the script to match your environment.

Run the script using PowerShell:
.\PasswordExpiryNotification.ps1
