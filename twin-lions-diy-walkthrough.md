# Build Your Own Budget Generator: Step-by-Step Walkthrough

This guide walks you through creating your own AI-powered Budget Generator using your actual project data—including branded PDF export for client-ready estimates and a streamlined workflow for keeping your pricing data current.

---

## Overview

**What you're building:** A Claude Project that generates accurate budget ranges for new projects based on your historical pricing data, with the ability to export branded PDF estimates.

**Key innovation:** Your pricing catalogue lives in SharePoint, and after each completed project, you simply drop your budget documents into Claude and run the "Update Catalogue" command. Claude extracts the costs and gives you ready-to-paste rows—no manual data entry.

**Time required:**
- Initial setup: 3-4 hours
- Per project update: 2-3 minutes (just drop documents and paste results)
- Quarterly review: 30 minutes

**What you'll need:**
- Access to Claude (claude.ai) with a Pro or Team subscription
- Access to SharePoint (for hosting your pricing catalogue)
- 10-15 completed project files (budgets, invoices, cost breakdowns)
- Your company's brand assets (logo, colors, fonts)

---

## Phase 1: Create Your Pricing Spreadsheet in SharePoint

### Step 1.1: Gather Your Source Documents

Pull together documents from 10-15 completed projects. For each project, you want:
- Original budget or estimate
- Final invoices and cost breakdown
- Change orders (if any)
- Notes on quality tier (was this a budget job, mid-range, or high-end?)

**Tip:** Start with projects from the last 12-18 months for current pricing. Older projects may have outdated costs.

### Step 1.2: Use Claude to Build Your Template

Open Claude (regular chat, not a Project yet) and use this prompt:

```
I'm building a pricing catalogue for my renovation company. I want to create a spreadsheet template that captures our costs across different categories and quality tiers.

Here's a sample budget document from a recent project:

[PASTE YOUR BUDGET DOCUMENT HERE]

Based on this, please:
1. Identify all the cost categories and line items
2. Create a CSV template with these columns:
   - Category
   - Item
   - Description
   - Unit (sq ft, linear ft, each, lump sum, etc.)
   - Budget Price
   - Mid-Range Price
   - Luxury Price
   - Last Updated (date)
   - Source (project name or supplier)
   - Notes

Format the output as a CSV I can copy into a spreadsheet.
```

**What to paste:** Copy and paste an actual budget document from one of your projects. Include as much detail as possible—line items, quantities, costs.

### Step 1.3: Refine the Template

Claude will generate a template based on your budget. Review it and ask for adjustments:

```
This is good. Please also add categories for:
- [Any categories you noticed are missing]
- [Specific items you commonly quote]

And remove:
- [Any categories that don't apply to your work]
```

### Step 1.4: Create the Spreadsheet in SharePoint

1. Go to your company SharePoint site
2. Navigate to a document library (or create one called "Pricing Data")
3. Create a new Excel workbook: `[YourCompany]-pricing-catalogue.xlsx`
4. Paste Claude's template into the first sheet
5. Name the sheet "Catalogue"
6. Format as a table (select all data, Insert > Table)

**Why SharePoint?**
- Version history—you can always see what changed and when
- Accessible from anywhere
- Easy to share with team members who need it
- Can be connected to Power Automate for advanced workflows later

---

## Phase 2: Populate with Historical Data

### Step 2.1: Bulk Process Your Historical Projects

Instead of processing projects one at a time, batch them together. Open Claude and use this prompt:

```
I'm building a pricing database from historical projects. I'm going to paste several project cost breakdowns. For each one, extract the costs and calculate per-unit pricing.

For each project, I'll tell you:
- Project type
- Square footage
- Quality tier (Budget / Mid-Range / Luxury)
- Completion date

Output format for each line item:
Category | Item | Unit | Per-Unit Cost | Quality Tier | Source Project | Date

Ready for the first project.
```

Then paste each project's data:

```
Project 1: Kitchen Renovation
- Square footage: 180 sq ft
- Quality tier: Mid-Range
- Completed: March 2025

[PASTE BUDGET/INVOICE DETAILS]
```

### Step 2.2: Copy Results to SharePoint

As Claude processes each project, it will output formatted rows. Copy these directly into your SharePoint spreadsheet, placing each price in the appropriate tier column (Budget, Mid-Range, or Luxury).

### Step 2.3: Let Claude Identify Averages and Outliers

After processing several projects, ask Claude:

```
I've processed all my historical projects. Now I need to establish final pricing tiers.

Here are my data points for each category (I'll paste my spreadsheet):

[PASTE YOUR CURRENT SPREADSHEET DATA]

For items with multiple data points:
1. Calculate recommended Budget, Mid-Range, and Luxury prices
2. Flag any outliers I should investigate
3. Note items with only one data point (less reliable)
4. Identify gaps where I have no data

Output as a clean table I can paste back into my spreadsheet.
```

---

## Phase 3: Fill Gaps in Your Data

### Step 3.1: Identify Missing Items

Review your spreadsheet. You'll likely have gaps—items that didn't appear in your sample projects but you still need to quote.

### Step 3.2: Research Missing Prices

For items with no historical data, you have options:

**Option A: Use supplier quotes**
Get current quotes from your suppliers and enter those costs plus your markup.

**Option B: Ask Claude to estimate (use cautiously)**
```
I need to add pricing for [ITEM] to my catalogue. I don't have historical data for this.

For context, here are some related items from my catalogue:
- [Similar item 1]: Budget $X, Mid $Y, Luxury $Z
- [Similar item 2]: Budget $X, Mid $Y, Luxury $Z

Based on typical industry relationships, what would be reasonable pricing tiers for [ITEM]?

Note: I'll verify this against supplier quotes before finalizing.
```

**Important:** Always verify Claude's estimates against real quotes. Mark estimated prices in your Notes column with "ESTIMATE - verify" so you know to update them when you get real data.

---

## Phase 4: Create Your Brand Guide

Your Brand Guide tells Claude how to format client-facing documents. This ensures every PDF estimate looks professional and consistent with your company's identity.

### Step 4.1: Gather Your Brand Assets

Collect:
- Your logo file (PNG with transparent background)
- Brand colors (hex codes like #2a4930)
- Font names (e.g., Montserrat, Open Sans)
- Taglines or key messaging
- Any awards or credentials to highlight

**Finding your colors:** If you don't know your hex codes, use a tool like [imagecolorpicker.com](https://imagecolorpicker.com) to extract colors from your logo or website.

### Step 4.2: Use Claude to Create Your Brand Guide

Use this prompt:

```
I need to create a brand guide document for my company that will be used to format client-facing PDF estimates. Here's my company information:

Company Name: [YOUR COMPANY NAME]
Industry: [e.g., Residential Renovation, Custom Home Building]
Location: [City/Region]

Brand Colors:
- Primary: [HEX CODE] - used for [headers, accents, etc.]
- Secondary: [HEX CODE] - used for [buttons, highlights, etc.]
- Text colors: [HEX CODES for dark text, light text, etc.]

Fonts:
- Primary font: [FONT NAME]
- Weights used: [Bold, Regular, etc.]

Tagline: [YOUR TAGLINE]

Awards/Credentials: [Any to highlight]

Tone of voice: [e.g., Professional but approachable, focuses on quality and transparency]

Please create a comprehensive brand guide in markdown format that includes:
1. Brand overview
2. Color palette with hex codes and usage rules
3. Typography specifications
4. Document structure for budget estimate PDFs
5. Writing style guidelines
6. Table formatting standards
7. PDF export specifications (file naming, required sections, disclaimers)
8. Contact information block format
9. Quality tier descriptions that match our brand voice
```

### Step 4.3: Review and Customize

Claude will generate a brand guide. Review it and ask for adjustments:

```
This is good. Please update:
- [Any colors that need adjustment]
- [Any messaging that doesn't fit your voice]
- [Any sections to add or remove]

Also add a standard disclaimer that reads:
"[YOUR PREFERRED DISCLAIMER TEXT]"
```

### Step 4.4: Save Your Brand Guide

1. Copy Claude's output
2. Save as `[YourCompany]-brand-guide.md`
3. Also upload to your SharePoint "Pricing Data" folder for safekeeping

---

## Phase 5: Set Up Your Claude Project

### Step 5.1: Create the Project

1. Go to [claude.ai](https://claude.ai)
2. Click **Projects** in the left sidebar
3. Click **+ New Project**
4. Name it: "[Your Company] Budget Generator"

### Step 5.2: Add Project Instructions

Click on **Project instructions** and paste the following (customize the bracketed sections):

```
## Your Role

You are a budget estimation assistant for [YOUR COMPANY NAME], a [TYPE OF COMPANY - e.g., residential renovation company]. Your job is to generate accurate budget ranges based on our actual pricing data.

You have access to:
- **Pricing Catalogue**: Our actual costs for materials, labour, and services
- **Brand Guide**: Our visual identity and document formatting standards

Quality tiers:
- **Budget**: Basic, cost-effective options
- **Mid-Range**: Quality materials balancing value and aesthetics
- **Luxury**: Premium materials and custom work

## Critical Rules

1. **ONLY use pricing from the provided catalogue.** Never use internet prices or general knowledge. If an item isn't in the catalogue, say so.

2. **Always present ranges, not single numbers.** Show Budget through Luxury so clients understand options.

3. **Ask questions before assuming.** When scope is unclear, ask rather than guess.

4. **Flag missing items.** If something isn't in the pricing data, note it as "Price TBD - not in catalogue."

5. **Follow brand guidelines.** When generating PDF-ready content, use the formatting, colors, and language specified in the Brand Guide.

## How to Generate a Budget

### Step 1: Gather Scope
Ask about:
- Project type and square footage
- Scope details (what's being done)
- Quality level preference
- Any specific selections already made

### Step 2: Build the Budget
- List applicable categories
- Calculate quantities from measurements
- Show all three tiers
- Add permits, project management, contingency

### Step 3: Present Clearly
Use tables. Show category subtotals. Include a summary at the top. Note any assumptions.

## PDF Export

When asked to "export as PDF" or "make this client-ready":
1. Reformat the budget following the Brand Guide specifications
2. Include the company logo in the header
3. Include all required sections (cover, summary, breakdown, notes, terms, contact)
4. Use brand colors, fonts, and tone of voice
5. Include the standard disclaimer
6. Provide instructions for finalizing the PDF

## Standard Additions
- Permits: 1.5% of construction value
- Project Management: 8% (Budget), 10% (Mid-Range), 12% (Luxury)
- Contingency: 10% (Budget), 15% (Mid-Range), 20% (Luxury)

## Update Catalogue Command

When the user says "update catalogue" or "add project to catalogue":
1. Ask them to paste their completed project documents (budget, invoices, cost breakdown)
2. Ask for: project type, square footage, quality tier, completion date
3. Extract per-unit costs for each line item
4. Output as CSV-formatted rows ready to paste into the spreadsheet:
   Category,Item,Description,Unit,Budget Price,Mid-Range Price,Luxury Price,Last Updated,Source,Notes
5. Only populate the price column matching the project's quality tier
6. Flag any items not currently in the catalogue as "NEW ITEM"
7. Flag any prices that differ >20% from catalogue as "PRICE VARIANCE - review"

## Important
- Round to reasonable precision (not $1,847.23—use $1,850)
- These are estimates for budgeting, not formal quotes
- Remind users that actual costs depend on site conditions and final selections
- Always follow the Brand Guide for tone, language, and formatting
```

### Step 5.3: Upload Your Project Files

Click **Add content** or the **+** button and upload:

| File | Purpose |
|------|---------|
| `[YourCompany]-pricing-catalogue.xlsx` | Your pricing data (download from SharePoint) |
| `[YourCompany]-brand-guide.md` | Your brand standards for PDF export |
| Company logo (PNG) | For PDF headers |

**Important:** When your SharePoint catalogue is updated, download the latest version and re-upload to keep Claude current.

### Step 5.4: Test Budget Generation

Start a new conversation in the Project and try:

```
I need a budget range for a main bathroom renovation. About 60 square feet, full gut, keeping plumbing in current locations, converting tub to walk-in shower. Mid-range finishes.
```

Claude should:
- Ask any clarifying questions
- Generate a budget using YOUR prices
- Show all three tiers
- Flag any items not in your catalogue

### Step 5.5: Test PDF Export

After Claude generates a budget, try:

```
Export this as a PDF for the client. Their name is John Smith.
```

Claude should:
- Reformat the budget following your brand guide
- Include all required sections
- Provide instructions for finalizing the PDF
- Suggest a filename following your naming convention

---

## Phase 6: The "Update Catalogue" Workflow

This is the key workflow that makes maintenance effortless. After completing any project, you simply drop your documents into Claude and get ready-to-paste data for your SharePoint spreadsheet.

### How It Works

1. **Complete a project** and gather your final documents (budget, invoices, cost breakdown)
2. **Open your Claude Project** (the Budget Generator)
3. **Say "update catalogue"** and paste your documents
4. **Claude extracts the data** and outputs CSV-formatted rows
5. **Open your SharePoint spreadsheet** and paste the new rows
6. **Download and re-upload** the updated spreadsheet to Claude (takes 30 seconds)

### Step 6.1: Run the Update Catalogue Command

In your Claude Project, start a new conversation:

```
Update catalogue
```

Claude will ask for your project documents. Paste everything:

```
Here's the completed project data:

Project: Main Floor Bathroom Renovation
Address: 123 Example Street
Square footage: 55 sq ft
Quality tier: Mid-Range
Completed: July 2025

[PASTE YOUR FINAL BUDGET/INVOICES]
```

### Step 6.2: Review Claude's Output

Claude will output something like:

```csv
Category,Item,Description,Unit,Budget Price,Mid-Range Price,Luxury Price,Last Updated,Source,Notes
Demolition,Bathroom demo,Full gut demo including fixtures,sq ft,,$12.50,,2025-07,123 Example St,
Plumbing,Rough-in,Shower valve and drain relocation,each,,$850,,2025-07,123 Example St,
Plumbing,Fixtures - shower,Shower trim and head install,each,,$425,,2025-07,123 Example St,
Tile,Floor tile,Porcelain tile installed,sq ft,,$18.75,,2025-07,123 Example St,
Tile,Wall tile,Subway tile to ceiling,sq ft,,$22.00,,2025-07,123 Example St,
...

NOTES:
- "Heated floor mat" is NEW ITEM - not in current catalogue
- "Tile installation" shows PRICE VARIANCE: catalogue has $16.50/sq ft, this project was $18.75/sq ft (14% higher)
```

### Step 6.3: Paste into SharePoint

1. Open your SharePoint pricing catalogue
2. Find the appropriate rows (or scroll to bottom for new items)
3. Paste Claude's output or manually enter the values
4. For price variances, decide whether to:
   - Update the catalogue price (if the new price reflects current market)
   - Keep the old price (if this project had unusual circumstances)
   - Average the two prices

### Step 6.4: Sync Claude's Copy

After updating SharePoint:
1. Download the updated spreadsheet
2. In your Claude Project, remove the old pricing catalogue
3. Upload the new version

**Tip:** Do this weekly rather than after every project if you're processing many jobs.

---

## Advanced: Automate with SharePoint + Power Automate (Optional)

For teams that want even less manual work, you can set up a Power Automate flow:

### Option A: Manual Trigger Flow
1. Create a flow triggered by a button in SharePoint
2. Flow downloads the catalogue, calls Claude API, and returns processed data
3. You still manually paste, but the Claude step is automated

### Option B: Folder Watch Flow
1. Create a "Completed Projects" folder in SharePoint
2. Flow triggers when documents are added
3. Sends documents to Claude API for processing
4. Appends results to your pricing catalogue automatically

**Note:** These advanced flows require:
- Power Automate premium (for HTTP connectors)
- Claude API access (separate from claude.ai subscription)
- Some technical setup

For most teams, the manual "Update Catalogue" workflow is fast enough and requires no additional subscriptions.

---

## Maintaining Your System

### After Every Completed Project (2-3 minutes)

1. Open Claude Project
2. Run "update catalogue" with your documents
3. Paste results into SharePoint
4. Re-upload catalogue to Claude (weekly is fine)

### Monthly Quick Check (15 minutes)

- Spot-check 5-10 items against recent invoices
- Update any prices that have drifted
- Review "ESTIMATE - verify" notes and update with real data

### Quarterly Review (30 minutes)

- Get fresh quotes from main suppliers
- Update material costs that have changed significantly
- Archive items you no longer offer
- Add items for new services

### When Branding Changes

1. Update your brand guide document
2. Re-upload to the Claude Project
3. Test with a PDF export to verify

---

## Troubleshooting

### Claude gives prices that seem wrong
- Check if the item exists in your catalogue (exact name match matters)
- Verify the unit of measure is correct
- Make sure you've uploaded the latest catalogue version

### Claude says it can't find an item
- Add the item to your catalogue
- Or try different wording (Claude matches on the item name in your CSV)

### Budgets are consistently too high/low
- Compare recent actuals to catalogue prices
- Your contingency percentages may need adjustment
- Some categories may have outdated pricing

### "Update catalogue" isn't extracting costs correctly
- Make sure you're providing complete documents (not just summaries)
- Include quantities and totals, not just unit prices
- Tell Claude the quality tier so it knows which column to populate

### Team members get different results
- Make sure everyone is using the same Project (not regular Claude chat)
- Verify everyone has the latest version of the catalogue uploaded

### PDF formatting looks off
- Check that your brand guide is uploaded to the Project
- Make sure the logo file is uploaded
- Use clear trigger phrases like "export as PDF" or "make this client-ready"

---

## Quick Reference: Key Commands

### Update catalogue after a completed project:
```
Update catalogue

[PASTE: Project details, final budget, invoices]
```

### Generate a budget:
```
Budget for [PROJECT TYPE]: [SIZE], [SCOPE DETAILS], [QUALITY LEVEL].
```

### Generate budget + PDF in one step:
```
Budget for [PROJECT TYPE]: [SIZE], [SCOPE DETAILS], [QUALITY LEVEL].
After you generate it, format as a client-ready PDF for [CLIENT NAME].
```

### Compare catalogue to actual costs:
```
Compare these actual costs to the catalogue and flag any significant differences (>15%):

[PASTE ACTUAL COSTS]
```

### Check for items needing updates:
```
Review the catalogue and list any items where:
- Last Updated is older than 12 months
- Notes say "ESTIMATE - verify"
- We have only one data point
```

---

## Summary: Your Workflow

### Build Once (3-4 hours)
1. Create pricing template from historical projects
2. Set up spreadsheet in SharePoint
3. Process 10-15 projects to populate data
4. Create brand guide
5. Set up Claude Project with catalogue, brand guide, and logo

### Use Daily
- Generate budgets using your real data
- Export client-ready PDFs with your branding

### After Each Project (2-3 minutes)
1. Run "update catalogue" in Claude
2. Paste your project documents
3. Copy Claude's output to SharePoint
4. Re-upload catalogue weekly

### Quarterly (30 minutes)
- Review prices against current supplier quotes
- Clean up estimates and single-data-point items
- Update brand guide if needed

---

The more projects you process, the more accurate your budgets become. The SharePoint + Claude workflow means that accuracy improvement happens almost automatically—just drop your documents in and paste the results.
