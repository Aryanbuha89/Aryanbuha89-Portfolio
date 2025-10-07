# EmailJS Setup Guide for Portfolio Contact Form

## Current Status
✅ **Contact form is now working with mailto fallback**
- Form validation works
- Success/error messages display properly
- Opens user's email client automatically
- Form resets after submission

## To Enable Direct Email Sending (Optional)

If you want emails to be sent directly without opening the email client, follow these steps:

### 1. Create EmailJS Account
1. Go to [EmailJS.com](https://www.emailjs.com/)
2. Sign up for a free account
3. Verify your email address

### 2. Set Up Email Service
1. In EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions
5. Note down your **Service ID**

### 3. Create Email Template
1. Go to "Email Templates"
2. Click "Create New Template"
3. Use this template structure:
```
Subject: New Portfolio Contact from {{from_name}}

From: {{from_name}}
Email: {{from_email}}

Message:
{{message}}
```
4. Note down your **Template ID**

### 4. Get Public Key
1. Go to "Account" → "General"
2. Copy your **Public Key**

### 5. Update Your Code
In `index.html`, replace the commented section with:

```javascript
// Initialize EmailJS
(function() {
  emailjs.init({
    publicKey: "YOUR_ACTUAL_PUBLIC_KEY", // Replace with your actual public key
  });
})();
```

And update the service/template IDs in the emailjs.send() function:
```javascript
emailjs.send(
  'YOUR_SERVICE_ID',  // Replace with your actual service ID
  'YOUR_TEMPLATE_ID', // Replace with your actual template ID
  templateParams,
  'YOUR_PUBLIC_KEY'   // Replace with your actual public key
)
```

## Current Working Solution
The contact form currently uses a **mailto** approach which:
- ✅ Works immediately without any setup
- ✅ Opens the user's default email client
- ✅ Pre-fills subject and message
- ✅ Shows proper success messages
- ✅ Validates form fields
- ✅ Has good user experience

This is a reliable fallback that works on all devices and doesn't require any API keys or external services.
