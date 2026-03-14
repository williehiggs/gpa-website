# GPA SMS Website — Deployment Guide

## What's In This Folder
11 HTML files that make up the full GPAsms.com website:

| File | Page |
|------|------|
| index.html | Homepage (main landing page) |
| about.html | About / Founder Story |
| services.html | All Services (SMS, Calling, Email, etc.) |
| contact.html | Contact Form |
| case-studies.html | Client Case Studies |
| partners.html | Partner Program |
| partner-apply.html | Partner Application Form |
| careers.html | Open Positions |
| resources.html | Blog / Articles |
| privacy.html | Privacy Policy |
| terms.html | Terms of Service |

---

## Step-by-Step: Get This Live on Vercel

### Step 1: Create the GitHub Repo

1. Go to **github.com** and log in
2. Click the **+** icon (top right) → **New repository**
3. Name it: `gpa-website`
4. Set to **Public** or **Private** (either works)
5. Do NOT check "Add a README" (we have one)
6. Click **Create repository**

### Step 2: Push the Files

Open your terminal and run these commands one at a time:

```bash
# Navigate to wherever you downloaded this folder
cd ~/Downloads/gpa-deploy

# Initialize git
git init

# Add all files
git add .

# Commit
git commit -m "Initial site launch"

# Connect to your GitHub repo (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/gpa-website.git

# Push
git branch -M main
git push -u origin main
```

### Step 3: Deploy on Vercel

1. Go to **vercel.com** and log in (use your GitHub account)
2. Click **Add New → Project**
3. Find **gpa-website** in your repo list and click **Import**
4. Framework Preset: select **Other**
5. Leave all other settings as default
6. Click **Deploy**
7. Wait 30-60 seconds — your site is live on a `.vercel.app` URL

### Step 4: Connect Your Domain (GPAsms.com)

1. In Vercel, go to your project → **Settings** → **Domains**
2. Type `gpasms.com` and click **Add**
3. Vercel will show you DNS records to add. You have two options:

**Option A — Nameservers (Recommended)**
- Go to wherever gpasms.com is registered (GoDaddy, Namecheap, etc.)
- Change the nameservers to the ones Vercel gives you
- This gives Vercel full DNS control (easiest)

**Option B — A Record + CNAME**
- Add an A record pointing `@` to `76.76.21.21`
- Add a CNAME record pointing `www` to `cname.vercel-dns.com`

4. Wait 5-30 minutes for DNS to propagate
5. Vercel auto-provisions SSL (HTTPS) — no action needed

### Step 5: Set Up globalprofitadvisors.com Redirect

1. In Vercel project → **Settings** → **Domains**
2. Add `globalprofitadvisors.com`
3. Vercel will ask — choose **Redirect to gpasms.com**
4. Update DNS for globalprofitadvisors.com the same way (nameservers or A/CNAME)

---

## How to Make Future Updates

When you get updated files from Claude:

```bash
cd ~/path-to/gpa-website

# Replace the updated files in the folder

# Then push
git add .
git commit -m "Update: description of changes"
git push
```

Vercel auto-deploys within 30 seconds of every push. No manual steps needed.

---

## Placeholders Still Needing Your Input

Search for these in the code and replace them:

| Placeholder | Where | What to Replace With |
|-------------|-------|---------------------|
| `YOUR_GHL_WEBHOOK_URL_HERE` | contact.html, partner-apply.html, index.html (exit popup + footer) | Your GoHighLevel webhook URLs |
| `GHL_CHAT_WIDGET_PLACEHOLDER` | All 11 pages | Your GHL chat widget embed code |
| `CJ_VIDEO_EMBED` | index.html | CJ's testimonial video embed |
| `502-370-5801` | All pages (nav + hero) | Replace with GHL tracking number when ready |

### How to Replace Webhooks
1. In GHL, create a webhook for each form (contact, partner app, exit popup, footer subscribe)
2. Open the HTML file in any text editor
3. Find `YOUR_GHL_WEBHOOK_URL_HERE`
4. Replace with your actual webhook URL (e.g., `https://services.leadconnectorhq.com/hooks/xxxxx`)
5. Save, git add, commit, push

### How to Add Chat Widget
1. Get your GHL chat widget embed code
2. Open each HTML file
3. Find `<!-- GHL_CHAT_WIDGET_PLACEHOLDER -->`
4. Replace that comment line with your embed code
5. Save, git add, commit, push

### How to Add CJ's Video
1. Upload CJ's video to YouTube or Vimeo
2. Open index.html
3. Find `CJ_VIDEO_EMBED`
4. Replace the play button div with an iframe embed
5. Save, git add, commit, push

---

## Domain Lookup Help

If you don't know where your domains are registered:
1. Go to https://who.is
2. Search `gpasms.com`
3. Look for "Registrar" — that's where you log in to manage DNS
4. Repeat for `globalprofitadvisors.com`
