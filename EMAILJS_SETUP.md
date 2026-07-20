# EmailJS Setup - Quick Reference

## 🔑 Step-by-Step Setup

### 1. Create Account
- Visit: https://www.emailjs.com/
- Sign up (free tier available)
- Verify your email

### 2. Create Email Service

**Dashboard → Email Services → Add Service**

- **Provider:** Gmail (or your email provider)
- Follow the authentication steps
- **Save your Service ID** (looks like: `service_xxxxxxx`)

### 3. Create Email Template

**Dashboard → Email Templates → Create New Template**

**Template Name:** Portfolio Contact Template

**Email Subject:**
```
New Message from Portfolio - {{subject}}
```

**Email Content:**
```
Hello,

You have received a new message from your portfolio contact form.

Sender Name: {{from_name}}
Sender Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
Best regards,
Your Portfolio
```

**Save Template ID** (looks like: `template_xxxxxxx`)

### 4. Get Public Key

**Dashboard → Account → Copy Public Key**

Public key looks like: `xxxxxxxxxxxxxxx`

### 5. Update Your Code

**Open: script.js**

**Line 6:** Update initialization
```javascript
emailjs.init("YOUR_PUBLIC_KEY_HERE");
```

**Around Line 120:** Update service and template IDs
```javascript
const response = await emailjs.send(
    'service_YOUR_SERVICE_ID',      // ← Replace this
    'template_YOUR_TEMPLATE_ID',    // ← Replace this
    templateParams
);
```

**Line 148:** Update recipient email
```javascript
to_email: 'vinamrnaik206@gmail.com' // ← Change to your email
```

### 6. Test Form

1. Open portfolio in browser
2. Scroll to Contact section
3. Fill form and submit
4. Check your email

---

## 📋 Template Variables

These variables are used in your email template:

| Variable | Source |
|----------|--------|
| `{{from_name}}` | Name field |
| `{{from_email}}` | Email field |
| `{{subject}}` | Subject field |
| `{{message}}` | Message textarea |
| `{{to_email}}` | Your email (your choice) |

---

## 🔒 Security Notes

✅ **Safe to share publicly:**
- Public Key (it's meant to be public)
- Service ID
- Template ID

❌ **Never share:**
- Your actual email password (use Gmail app password instead)
- Private EmailJS keys (you don't have any)

---

## 💰 EmailJS Pricing

**Free Plan:**
- 200 emails/month
- 3 email services
- Unlimited templates
- Basic support

**Perfect for personal portfolios!**

---

## 🐛 Troubleshooting

### "Failed to send message"
- ✓ Check Service ID is correct
- ✓ Check Template ID is correct
- ✓ Check Public Key is correct
- ✓ Verify email service is connected
- ✓ Check browser console for errors

### "CORS error"
- This usually means EmailJS.com is being blocked
- Check your email service authentication
- Restart your browser

### Not receiving emails
- Check spam folder
- Verify recipient email in code
- Check EmailJS dashboard for delivery reports
- Ensure email service is active

---

## 📧 Gmail App Password (Recommended)

If using Gmail:
1. Enable 2-factor authentication
2. Create app-specific password
3. Use that in EmailJS setup (not your regular password)

---

## 🔗 Useful Links

- EmailJS Dashboard: https://dashboard.emailjs.com/
- Documentation: https://www.emailjs.com/docs/
- Status Page: https://status.emailjs.com/

---

**Need Help?**
- EmailJS Support: support@emailjs.com
- Check console errors (F12 → Console tab)

