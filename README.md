# ExamCracker — SSC CGL Mock Test Platform
### Complete Deployment & Usage Guide

---

## 📁 Files in This Package

| File | Purpose |
|------|---------|
| `index.html` | Main website — Landing page + Exam interface + Results + Dashboard |
| `admin.html` | Admin panel — Generate keys, view results, export data |
| `Code.gs` | Google Apps Script backend — Paste into script.google.com |
| `Image1.png` | Replace with your motivational image 1 |
| `Image2.png` | Replace with your motivational image 2 |
| `Image3.png` | Replace with your motivational image 3 |

---

## ⚡ Quick Start (Without Google Sheets)

The website works RIGHT NOW without any setup.
Open `index.html` in your browser and test everything.

### Demo Keys for Testing:
```
SSC2024DEMO
EXAMCRACKER49
TESTKEY001
```

Enter any of these on the Key Login page to access the paid dashboard.

---

## 🔧 Full Setup (With Google Sheets)

### Step 1 — Create Google Sheet

1. Go to https://sheets.google.com
2. Create new spreadsheet → name it **ExamCracker Database**
3. Create 3 tabs at the bottom:
   - `Questions`
   - `Keys`
   - `Results`

### Step 2 — Add Column Headers

**Questions sheet — Row 1:**
```
Question_ID | Subject | Year | Question | Option_A | Option_B | Option_C | Option_D | Correct_Answer | Explanation | Difficulty | Paper
```
> Correct_Answer: 0=A, 1=B, 2=C, 3=D

**Keys sheet — Row 1:**
```
Key | Status | Purchase_Date | Student_Name | Attempts | Expiry_Date
```
> Status values: Active / Inactive

**Results sheet — Row 1:**
```
Key | Test_Name | Date | Total_Questions | Correct | Wrong | Unattempted | Score | Percentage | Time_Taken
```

### Step 3 — Deploy Google Apps Script

1. Go to https://script.google.com → New Project
2. Delete any existing code
3. Paste entire content of `Code.gs`
4. Replace `YOUR_SHEET_ID_HERE` with your Sheet ID
   - Sheet ID is in the URL: `docs.google.com/spreadsheets/d/SHEET_ID_HERE/edit`
5. Click **Deploy → New Deployment**
   - Type: Web App
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Click Deploy → Copy the Web App URL

### Step 4 — Connect Website

In `index.html`, find this line (around line 1050 in the script section):
```javascript
const APPS_SCRIPT_URL = '';
```
Replace with your URL:
```javascript
const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec';
```

### Step 5 — Update Your Contact Details

In `index.html`, search for and replace:
```
yourUPI@bank        → Your actual UPI ID (e.g. yourname@paytm)
+91 XXXXXXXXXX      → Your WhatsApp number
examcracker.github.io → Your actual GitHub Pages URL
```

### Step 6 — Deploy on GitHub Pages (FREE hosting)

1. Create account at https://github.com
2. Create new repository → name: `examcracker` (or any name)
3. Upload these files:
   - `index.html`
   - `admin.html`
   - `Image1.png`, `Image2.png`, `Image3.png`
4. Go to repository **Settings → Pages**
5. Source: Deploy from branch → Branch: **main** → Folder: **/ (root)**
6. Click Save
7. Your site is live at: `https://yourusername.github.io/examcracker`

---

## 💼 Daily Workflow (After Setup)

### When a student wants to subscribe:
```
Student clicks "Subscribe ₹49"
       ↓
Modal shows your UPI ID + WhatsApp number
       ↓
Student pays ₹49 → sends screenshot on WhatsApp
       ↓
You confirm payment
       ↓
Open admin.html → Generate Key → enter student name
       ↓
Copy the key → send on WhatsApp
       ↓
Student enters key on website → All papers unlock ✅
```

### To manage keys:
- Open `admin.html` (keep this file local, do NOT upload to GitHub)
- Default admin password: `examcracker2024` (change this!)
- Go to **Generate Key** tab → Enter student name → Generate → Copy → Send

---

## 🎨 Customization

### Change Platform Name
Search for `ExamCracker` in `index.html` and replace with your name.

### Change Colors
In `index.html`, find the `:root` CSS block and change:
```css
--primary: #1a3c6e;      /* Dark blue — main brand color */
--primary-light: #2558a8; /* Lighter blue */
--accent: #f5a623;        /* Orange/gold — buttons, highlights */
```

### Add Real Questions
Add questions directly to the **Questions** sheet in Google Sheets.
Each row = one question. Follow the column format above.
The website will automatically load them.

### Change Admin Password
In `admin.html`, find:
```javascript
const ADMIN_PASSWORD = 'examcracker2024';
```
Change to your own password.

---

## 📊 Scoring System
- ✅ Correct Answer: **+2 marks**
- ❌ Wrong Answer: **-0.5 marks**
- ⬜ Unattempted: **0 marks**
- Maximum Score per paper: **200 marks**

---

## 📱 Platform Features

### For Students
- ✅ Free trial — 1 complete paper, no login needed
- ✅ Real CBT interface (same as actual SSC CGL)
- ✅ Question palette — Green/Red/Purple/White status
- ✅ Section-wise navigation (Reasoning, Quant, English, GA)
- ✅ Mark for Review feature
- ✅ 60-minute countdown timer (turns red at 5 minutes)
- ✅ Offline-safe — test continues even if internet drops
- ✅ Instant result with score, accuracy, subject analysis
- ✅ WhatsApp score sharing
- ✅ Dashboard with performance history

### For Admin (You)
- ✅ Password-protected admin panel
- ✅ Generate single or bulk access keys
- ✅ Copy key + send via WhatsApp in one click
- ✅ View all results
- ✅ Export keys and results as CSV
- ✅ Deactivate keys
- ✅ Setup guide built-in

---

## 🔒 Security Notes

- Admin panel (`admin.html`) should stay on your local computer
- Do NOT upload `admin.html` to GitHub (or set it private)
- The Google Apps Script handles key validation server-side
- Trial attempts are tracked via browser localStorage
- For stronger security later, add Google reCAPTCHA

---

## 🚀 Future Expansion Ready

When you want to add more features later:
- **More exam types**: SSC CHSL, Railway — just add questions with different `Paper` column values
- **Leaderboard**: Add a leaderboard sheet and display top scores
- **Email reports**: Use Apps Script's MailApp to email results
- **More papers**: Add questions to Google Sheet — no code changes needed

---

## 📞 Support

If anything breaks or you need help:
- Check the **Setup Guide** tab inside `admin.html`
- All settings to change are marked with `// ← CHANGE THIS` in the code

---

*ExamCracker — Not affiliated with Staff Selection Commission (SSC)*
*For queries: Contact on WhatsApp*
