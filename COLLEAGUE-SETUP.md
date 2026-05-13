# LiveScapeOS — Colleague Setup Guide

Everything you need to get up and running. Follow the steps in order, then use the prompts below for your day-to-day work.

---

## Step 1: Install Claude Code

Download the Claude Code desktop app:
**https://claude.ai/download**

Sign in with your Anthropic account. If you don't have one, create one at claude.ai.

---

## Step 2: Install Ruflo MCP

Open Claude Code and paste this prompt:

```
I'm setting up Ruflo for collaborative agent work. Install the Ruflo MCP into my Claude system using this command: claude mcp add claude-flow -- npx -y @claude-flow/cli@latest

Then start the daemon with: npx @claude-flow/cli@latest daemon start

Then verify everything is working with: npx @claude-flow/cli@latest doctor --fix

Tell me when it's done and show me the health status.
```

---

## Step 3: Authenticate GitHub

Open Claude Code and paste this prompt:

```
Set up GitHub authentication on my machine so I can clone and push to private repos. Run: gh auth login

Walk me through the browser authentication flow.
```

---

## Step 4: Clone LiveScapeOS

Open Claude Code and paste this prompt:

```
Clone the LiveScapeOS repository into my home directory and open it as my working directory.

Repo: https://github.com/iqbalaaameer/LiveScapeOS

After cloning, confirm:
1. The .claude/settings.json file is present with all 7 domain hooks
2. The Ruflo daemon is running
3. The domains/ folder structure is intact

List all available domains and tell me which ones are active.
```

---

## Step 5: Verify Setup

Once cloned, paste this final verification prompt:

```
I've just cloned LiveScapeOS. Verify my full setup is working:
1. Ruflo MCP is connected and daemon is running
2. All 7 domain hooks are active in .claude/settings.json
3. Memory namespaces are initialised
4. Run a test trigger by searching for any existing patterns in the entertainment-ops and artist-research namespaces

Tell me what shared knowledge already exists from previous sessions, and confirm I'm ready to start working.
```

---

## You're Set Up. Start Working.

From here, just paste any prompt below into Claude Code. Agents spawn automatically, load all shared team knowledge, and push their learnings back to GitHub when done — no manual steps needed.

---

## Domain 1: Entertainment Operations (P&Ls, Venue, Contracts)

### Generate a P&L
```
I need a P&L for [CONCERT TYPE] at [VENUE NAME / VENUE SIZE] with [TICKET PRICE] average pricing and [CAPACITY] capacity. Load all previous concert patterns and generate the full P&L with cost breakdown and margin analysis.
```

**Examples:**
```
I need a P&L for a hip-hop show at Stadium Putra (capacity 7000, avg ticket RM180). Load all previous concert patterns and generate the full P&L.
```
```
I need a P&L for a DJ night at a 500-cap club, avg ticket RM80. Load patterns and generate.
```

### Review a Contract
```
Review this artist contract for [ARTIST NAME]. Flag any unusual clauses, missing riders, or risk areas. Context: [VENUE], [DATE], [FEE].
```

### Venue Logistics
```
Plan the logistics for [SHOW NAME] at [VENUE]. Include load-in schedule, crew requirements, production checklist, and timeline.
```

---

## Domain 2: Artist Research

### Full Artist Brief
```
Research [ARTIST NAME] for a potential booking in [MARKET / CITY]. I need: fanbase size and demographics, recent touring history, comparable shows in SEA, recommended fee range, and any red flags. Load all previous artist patterns.
```

### Market Comparison
```
Compare [ARTIST A] vs [ARTIST B] for a [GENRE] show in [CITY]. Which has stronger draw? Which is better value? Recommend one with reasoning.
```

### Genre Trend Analysis
```
Analyse current [GENRE] market trends in [MARKET]. What artists are gaining momentum? What's the typical ticket price range? What venues are appropriate?
```

### Booking Strategy
```
We're considering booking [ARTIST] for [DATE] at [VENUE]. Build a booking strategy: recommended deal structure, support acts, ticket tiers, marketing angle.
```

---

## Domain 3: Financial Services *(coming soon)*

### Generate Invoice
```
Generate an invoice for [CLIENT NAME] for [SERVICE DESCRIPTION]. Amount: [MYR AMOUNT]. Payment terms: [NET 30 / NET 14]. Our entity: LiveScape Events Sdn Bhd.
```

### Cash Flow Forecast
```
Build a cash flow forecast for [MONTH/QUARTER]. Inputs: [list of expected income and expenses]. Highlight any float risk periods.
```

---

## Domain 4: Product Development *(coming soon)*

### Landing Page Brief
```
Build a landing page brief for [PRODUCT NAME]. Audience: [TARGET USER]. Goal: [CONVERSION ACTION]. Key message: [MAIN VALUE PROP].
```

---

## Domain 5: Digital Marketing *(coming soon)*

### Campaign Brief
```
Build a campaign brief for [SHOW / PRODUCT]. Goal: [TICKET SALES / AWARENESS / LEADS]. Budget: [MYR AMOUNT]. Channels: [IG / TikTok / Meta Ads / Email]. Timeline: [WEEKS].
```

### Content Calendar
```
Build a 4-week content calendar for [SHOW / BRAND]. Platform: [IG / TikTok / LinkedIn]. Tone: [HYPE / EDUCATIONAL / BEHIND THE SCENES].
```

---

## Domain 6: Agency Services *(coming soon)*

### Brand Strategy
```
Develop a brand strategy for [CLIENT]. Current positioning: [DESCRIBE]. Target audience: [WHO]. Competitors: [LIST].
```

### Pitch Document
```
Write a pitch for [CLIENT / PROSPECT]. Service: [WHAT WE'RE PITCHING]. Deliverables: [LIST]. Budget range: [MYR AMOUNT].
```

---

## How Shared Learning Works

Every time you complete a task, the agents automatically:
1. Store what they learned in the shared memory
2. Push those learnings to the LiveScapeOS GitHub repo

This means when your colleague runs their next task, their agents already know everything you've learned — and vice versa. The more you use it, the smarter the agents get for everyone.

---

## Already Set Up and Need to Update?

If you were already using LiveScapeOS and need to pull the latest changes:

```
Pull the latest LiveScapeOS changes from GitHub, verify the Ruflo daemon is running, and confirm all 7 domain hooks are active in .claude/settings.json. Tell me which domains are now available and confirm the P&L workflow still works as before.
```
