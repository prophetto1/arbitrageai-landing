# EmailJS Contact Form Setup Guide

Your contact form has been updated with EmailJS integration! Follow these steps to complete the setup.

## 🚀 Quick Setup Steps

### 1. Create EmailJS Account
1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Sign up for a free account (200 emails/month free)
3. Verify your email address

### 2. Set up Email Service
1. In your EmailJS dashboard, go to **"Email Services"**
2. Click **"Add New Service"**
3. Choose your email provider (Gmail, Outlook, Yahoo, etc.)
4. Follow the setup instructions to connect your email
5. **Copy your Service ID** (you'll need this later)

### 3. Create Email Template
1. Go to **"Email Templates"** in your dashboard
2. Click **"Create New Template"**
3. Use this template setup:

**Template Name:** `contact_form`

**Subject:** `New Contact Form Submission - {{subject}}`

**Content:**
```
Hello ArbitrageAI Team,

You have received a new message from your website contact form.

From: {{from_name}}
Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from your ArbitrageAI website contact form.
```

4. Save the template and **copy your Template ID**

### 4. Get Your Public Key
1. Go to **"Account"** → **"General"**
2. Find and **copy your Public Key** (User ID)

### 5. Update Contact Component
Open `src/components/Contact.vue` and replace these values around line 30:

```typescript
// Replace these with your actual EmailJS values
const EMAILJS_SERVICE_ID = 'your_actual_service_id';
const EMAILJS_TEMPLATE_ID = 'your_actual_template_id';  
const EMAILJS_PUBLIC_KEY = 'your_actual_public_key';
```

### 6. Test Your Contact Form
1. Run your development server: `npm run dev`
2. Navigate to the contact section
3. Fill out and submit the form
4. Check your email for the message!

## 🎯 Features Implemented

✅ **Form Validation** - Checks required fields and email format  
✅ **Loading States** - Shows spinner during submission  
✅ **Success/Error Messages** - Clear user feedback  
✅ **Form Reset** - Clears form after successful submission  
✅ **Professional Email Format** - Structured email template  
✅ **Improved Subject Options** - Better categorization  
✅ **Accessibility** - Proper labels and form attributes  

## 📧 Optional: Auto-Reply Setup

You can create a second template for auto-replies:

1. Create another template called `auto_reply`
2. Use this content:

**Subject:** `Thank you for contacting ArbitrageAI`

**Content:**
```
Hello {{from_name}},

Thank you for reaching out to ArbitrageAI! We've received your message about "{{subject}}" and will get back to you within 24 hours.

In the meantime, feel free to explore our platform features and join our community for the latest updates.

Best regards,
The ArbitrageAI Team

---
This is an automated response. Please do not reply to this email.
```

Then add this to your Contact.vue after the main email is sent:

```typescript
// Send auto-reply
await emailjs.send(
  EMAILJS_SERVICE_ID,
  'auto_reply_template_id',
  {
    from_name: contactForm.firstName,
    from_email: contactForm.email,
    subject: contactForm.subject,
  },
  EMAILJS_PUBLIC_KEY
);
```

## 🔧 Troubleshooting

**Form not sending emails?**
- Check that all three IDs are correctly set
- Verify your email service is properly connected
- Check browser console for error messages

**Emails going to spam?**
- Add your domain to EmailJS allowed domains
- Set up SPF/DKIM records for your domain

**Need help?**
- Check EmailJS documentation: https://www.emailjs.com/docs/
- Test your setup in EmailJS dashboard first

## 💡 Pro Tips

- EmailJS free tier includes 200 emails/month
- You can track email delivery in the EmailJS dashboard
- Set up email templates for different subjects
- Consider adding a honeypot field for spam protection

---

Your contact form is now ready to receive and send professional emails! 🎉 