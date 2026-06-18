# PMOS™ — Project Management Operating System

**ERP & Transformation Behavioral Diagnostic**

> *Projects rarely fail because of technology. They fail because of five hidden behavioral patterns that no RAG status report will ever surface. PMOS identifies which ones are active in your program — scored, ranked, and translated into a recovery plan.*

---

## Live demo

**[→ Launch the diagnostic](https://YOUR-USERNAME.github.io/pmos)**

---

## What PMOS does

PMOS is a 7-question behavioral diagnostic for ERP and transformation programs. In under 4 minutes it produces:

**Free scan**
- Primary PMOS pattern — named and scored
- Go-live delay risk percentage
- First 2 sentences of the primary diagnosis
- Preview of 4 locked patterns

**Full report (paid)**
- All 5 PMOS pattern scores (0–100)
- PMOS Health Index — Governance, Decision Velocity, Adoption, Leadership, Execution
- Primary, secondary and tertiary diagnosis in executive language
- Most likely failure scenario — the 12-week collapse timeline
- All 5 risk forecasts: go-live delay, budget overrun, adoption failure, executive escalation, hero burnout
- Cost-of-delay calculator — financial exposure in £/$ from your program budget
- Verbatim steering committee talking points — 4 scenarios, ready to use
- 30-day recovery plan — week by week
- Top 3 actions for Monday morning
- Diagnosis-matched intervention playbooks

---

## The 5 PMOS Patterns

| Pattern | What it means |
|---|---|
| **Death By Governance™** | Too many meetings, reports and approvals. Too little action. |
| **Nobody Wants To Decide™** | Everyone is involved. Nobody owns the decision. |
| **Silent Resistance™** | The system changed. The behavior didn't. |
| **Hero Dependency™** | Two people are carrying the entire transformation. |
| **Builder Culture™** | Problems get solved instead of discussed. *(The healthy pattern.)* |

---

## Deploy to GitHub Pages in 5 minutes

### Prerequisites
- A GitHub account (free)
- Git installed, or use GitHub's web interface

### Step 1 — Create a new repository

Go to [github.com/new](https://github.com/new) and create a repository named `pmos`.

- **Repository name:** `pmos`
- **Visibility:** Public *(required for free GitHub Pages)*
- **Do NOT** initialise with README (you already have one)

### Step 2 — Upload the files

**Option A — GitHub web interface (no Git required)**

1. Open your new repository on GitHub
2. Click **Add file → Upload files**
3. Drag and drop `index.html` and `README.md`
4. Click **Commit changes**

**Option B — Git command line**

```bash
# Clone your new repo
git clone https://github.com/YOUR-USERNAME/pmos.git
cd pmos

# Copy the PMOS files into the repo
cp /path/to/index.html .
cp /path/to/README.md .

# Push
git add .
git commit -m "Launch PMOS v2 diagnostic"
git push origin main
```

### Step 3 — Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top tab)
3. Click **Pages** (left sidebar, under Code and automation)
4. Under **Source**, select **Deploy from a branch**
5. Under **Branch**, select **main** and **/ (root)**
6. Click **Save**

### Step 4 — Your URL is live

GitHub will display your URL at the top of the Pages settings page:

```
https://YOUR-USERNAME.github.io/pmos
```

It typically goes live within 1–3 minutes. GitHub sends no notification — just visit the URL.

### Step 5 — Update the meta tags (important)

Open `index.html` and replace `YOUR-USERNAME` with your actual GitHub username in these two lines:

```html
<meta property="og:url" content="https://YOUR-USERNAME.github.io/pmos">
<meta property="og:image" content="https://YOUR-USERNAME.github.io/pmos/og-image.png">
```

---

## Connect your Gumroad product (the paywall)

The "Unlock the full report" button currently simulates an instant unlock for demo purposes. To connect it to a real payment:

### Option A — Direct Gumroad link (simplest)

In `index.html`, find this line:

```javascript
function unlockReport(){
  // In production: redirect to Stripe/Gumroad checkout
  // For demo: simulate instant unlock
  state.isPaid = true;
  buildReport();
```

Replace `state.isPaid = true; buildReport();` with:

```javascript
window.location.href = 'https://YOUR-GUMROAD-USERNAME.gumroad.com/l/YOUR-PRODUCT-ID';
```

After purchase, Gumroad redirects buyers to a URL you specify. Set that redirect URL to `https://YOUR-USERNAME.github.io/pmos?paid=true`. Then add this to the top of your script:

```javascript
// Auto-unlock if returning from Gumroad
if(new URLSearchParams(window.location.search).get('paid')==='true'){
  state.isPaid = true;
}
```

### Option B — Stripe Checkout (recommended for scale)

Replace the `unlockReport()` function body with a redirect to your Stripe Payment Link. Stripe's redirect-after-payment URL works identically to Gumroad's.

Also update the "Get the Recovery Toolkit →" button link:

```html
href="https://YOUR-GUMROAD-LINK"
```

---

## Customise for your brand

All design tokens live at the top of the `<style>` block in `index.html`:

```css
:root {
  --navy:   #1A1A2E;   /* Primary brand colour */
  --red:    #E8505B;   /* Accent / CTA colour  */
  --orange: #E07B39;   /* Elevated band colour  */
  --amber:  #E8A33D;   /* Watch band colour     */
  --green:  #2E9E5B;   /* Healthy band colour   */
}
```

To change colours, update these six values. Everything else derives from them.

---

## Add an og-image for social sharing

When you share the link on LinkedIn, Slack or WhatsApp, it will pull the `og:image`. Create a 1200×630px PNG with the PMOS branding and upload it to your repository as `og-image.png`.

A quick approach:
1. Take a screenshot of the landing page at 1200px width
2. Name it `og-image.png`
3. Upload it to your repository root (same folder as `index.html`)

---

## File structure

```
pmos/
├── index.html        ← The complete PMOS application (single file)
└── README.md         ← This file
```

PMOS is intentionally a single-file application. No build step, no dependencies, no server. It runs entirely in the browser.

---

## Scoring engine

The PMOS diagnostic engine is deterministic and fully transparent:

- 7 questions → normalized scores (0–100 per question)
- 5 pattern scores computed from weighted sums of question responses
- Scoring weights validated against the known test case: answers (5,4,4,5,4,3,2) → DBG=90, NWD=85, SR=67.5, HD=95, BC=37.5
- Health Index = 5 derived scores from pattern scores
- Risk forecasts = weighted composites of pattern scores
- Cost-of-delay = program budget × delay risk × modelled multipliers

All weights are in the `WEIGHTS` object and `DIAGNOSIS_LIB` in the script block.

---

## Product suite

| Product | Price | What it contains |
|---|---|---|
| PMOS Quick Scan | Free | Go-live delay risk + primary pattern |
| PMOS Diagnostic Report | £/₹ varies | Full report (what the "Unlock" button delivers) |
| PMOS Recovery Toolkit | £/₹ varies | 10 step-by-step intervention playbooks |
| PMOS Operator System | £/₹ varies | Full engine + assessments + workshop guide |

---

## License

Single-purchaser license. Internal and client-facing use permitted. Redistribution of the source code is not permitted.

---

*PMOS™ — Project Management Operating System*
*Behavioral Diagnosis for ERP & Transformation Programs*
