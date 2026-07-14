# Build Your Own Budget Generator: Step-by-Step Walkthrough

This guide walks you through creating your own AI-powered Budget Generator using your actual project data—including branded PDF export for client-ready estimates and a fully automated workflow for keeping your pricing data current.

---

## Overview

**What you're building:** A Claude Project that generates accurate budget ranges for new projects based on your historical pricing data, with the ability to export branded PDF estimates.

**Key innovation:** Your pricing catalogue lives in SharePoint, and Claude connects to it directly via the SharePoint connector. After each completed project, you simply drop your budget documents into Claude and say "update catalogue"—Claude extracts the costs and updates your SharePoint spreadsheet automatically. No copying, no pasting, no manual data entry.

**Time required:**
- Initial setup: 3-4 hours
- Per project update: Under 1 minute (just drop files and confirm)
- Quarterly review: 30 minutes

**What you'll need:**
- Access to Claude (claude.ai) with a Pro or Team subscription
- SharePoint connector configured in Claude (MCP integration)
- 10-15 completed project files (budgets, invoices, cost breakdowns)
- Your company's brand assets (logo, colors, fonts)

---

## Prerequisites: SharePoint Connector

Before starting, ensure your SharePoint connector is configured in Claude. This allows Claude to:
- Read your pricing catalogue directly from SharePoint
- Write updates back to the spreadsheet automatically
- Access your brand guide and other project files

If you haven't set up the SharePoint connector yet, follow the MCP setup guide for your organization.

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
3. Create a new Excel workbook: `pricing-catalogue.xlsx`
4. Paste Claude's template into the first sheet
5. Name the sheet "Catalogue"
6. Format as a table (select all data, Insert > Table)
7. Note the file path—you'll need it for the Claude Project setup

**Why SharePoint with Claude connector?**
- Claude can read and write directly—no manual syncing
- Version history—you can always see what changed and when
- Accessible from anywhere
- Automatic backups

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

### Step 2.2: Add Results to SharePoint

Once Claude has processed your historical projects:

```
Now write these results to my SharePoint pricing catalogue at [YOUR SHAREPOINT PATH]/pricing-catalogue.xlsx

Place each price in the appropriate tier column based on the quality tier of the source project.
```

Claude will update your SharePoint spreadsheet directly.

### Step 2.3: Let Claude Identify Averages and Outliers

After processing several projects:

```
Read my pricing catalogue from SharePoint and analyze it:

1. For items with multiple data points, calculate recommended Budget, Mid-Range, and Luxury prices
2. Flag any outliers I should investigate
3. Note items with only one data point (less reliable)
4. Identify gaps where I have no data

Then update the catalogue with the recommended prices.
```

---

## Phase 3: Fill Gaps in Your Data

### Step 3.1: Identify Missing Items

Ask Claude to review your catalogue:

```
Read my pricing catalogue from SharePoint and list any common renovation items that are missing. Compare against typical bathroom, kitchen, and whole-home renovation scopes.
```

### Step 3.2: Research Missing Prices

For items with no historical data, you have options:

**Option A: Use supplier quotes**
Get current quotes from your suppliers and have Claude add them:

```
Add these supplier quotes to my pricing catalogue:

[ITEM]: $X per [UNIT] - source: [SUPPLIER NAME], date: [DATE]
[ITEM]: $X per [UNIT] - source: [SUPPLIER NAME], date: [DATE]

Mark these as "Supplier quote" in the Notes column.
```

**Option B: Ask Claude to estimate (use cautiously)**
```
I need to add pricing for [ITEM] to my catalogue. I don't have historical data for this.

Read the catalogue and find similar items, then suggest reasonable pricing tiers based on typical industry relationships.

Mark any estimates with "ESTIMATE - verify" in the Notes column.
```

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

### Step 4.3: Save Brand Guide to SharePoint

Save the brand guide to your SharePoint Pricing Data folder:

```
Save this brand guide to my SharePoint at [YOUR SHAREPOINT PATH]/brand-guide.md
```

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
- **Pricing Catalogue**: Located at [SHAREPOINT PATH]/pricing-catalogue.xlsx
- **Brand Guide**: Located at [SHAREPOINT PATH]/brand-guide.md
- **SharePoint Connector**: You can read from and write to our SharePoint directly

Quality tiers:
- **Budget**: Basic, cost-effective options
- **Mid-Range**: Quality materials balancing value and aesthetics
- **Luxury**: Premium materials and custom work

## Critical Rules

1. **ONLY use pricing from the catalogue.** Read the pricing catalogue from SharePoint. Never use internet prices or general knowledge. If an item isn't in the catalogue, say so.

2. **Always present ranges, not single numbers.** Show Budget through Luxury so clients understand options.

3. **Ask questions before assuming.** When scope is unclear, ask rather than guess.

4. **Flag missing items.** If something isn't in the pricing data, note it as "Price TBD - not in catalogue."

5. **Follow brand guidelines.** Read the brand guide from SharePoint when generating PDF-ready content.

## How to Generate a Budget

### Step 1: Gather Scope
Ask about:
- Project type and square footage
- Scope details (what's being done)
- Quality level preference
- Any specific selections already made

### Step 2: Build the Budget
- Read current prices from the SharePoint catalogue
- List applicable categories
- Calculate quantities from measurements
- Show all three tiers
- Add permits, project management, contingency

### Step 3: Present Clearly
Use tables. Show category subtotals. Include a summary at the top. Note any assumptions.

## PDF Export

When asked to "export as PDF" or "make this client-ready":
1. Read the brand guide from SharePoint
2. Reformat the budget following the Brand Guide specifications
3. Include the company logo in the header
4. Include all required sections (cover, summary, breakdown, notes, terms, contact)
5. Use brand colors, fonts, and tone of voice
6. Include the standard disclaimer
7. Provide instructions for finalizing the PDF

## Standard Additions
- Permits: 1.5% of construction value
- Project Management: 8% (Budget), 10% (Mid-Range), 12% (Luxury)
- Contingency: 10% (Budget), 15% (Mid-Range), 20% (Luxury)

---

## SKILL: Update Catalogue

**Trigger phrases:** "update catalogue", "add project to catalogue", "update pricing"

When the user triggers this skill:

### Step 1: Gather Project Information
Ask the user to provide (or upload files containing):
- Project type
- Square footage
- Quality tier (Budget / Mid-Range / Luxury)
- Completion date
- Final budget, invoices, or cost breakdown documents

The user may upload PDFs, spreadsheets, or paste text directly.

### Step 2: Extract Costs
From the provided documents:
- Identify all line items with costs
- Calculate per-unit pricing (total cost ÷ quantity)
- Categorize each item
- Note the unit of measure

### Step 3: Read Current Catalogue
Read the pricing catalogue from SharePoint at [SHAREPOINT PATH]/pricing-catalogue.xlsx

### Step 4: Compare and Prepare Updates
For each extracted item:
- Check if it exists in the catalogue
- If exists: Compare the new price to the existing price
  - Flag if difference > 20% as "PRICE VARIANCE"
- If new: Mark as "NEW ITEM"

### Step 5: Show Summary for Approval
Present a summary table showing:
| Item | Current Price | New Price | Variance | Action |
|------|--------------|-----------|----------|--------|
| [Item] | $X.XX | $Y.YY | +/-Z% | Update/Add/Skip |

Ask: "I found X items to update and Y new items to add. Should I proceed with updating the catalogue?"

### Step 6: Update SharePoint
Upon confirmation:
1. Write the updates to the pricing catalogue in SharePoint
2. Set "Last Updated" to today's date
3. Set "Source" to the project name/address
4. For price variances, update the appropriate tier column
5. For new items, add a new row

### Step 7: Confirm Completion
Report: "Catalogue updated successfully. X items updated, Y new items added. The changes are now live in SharePoint."

---

## Important Reminders
- Round to reasonable precision (not $1,847.23—use $1,850)
- These are estimates for budgeting, not formal quotes
- Remind users that actual costs depend on site conditions and final selections
- Always follow the Brand Guide for tone, language, and formatting
```

### Step 5.3: Upload Your Logo

Click **Add content** or the **+** button and upload:
- Company logo (PNG) - For PDF headers

Note: The pricing catalogue and brand guide are accessed directly from SharePoint via the connector, so you don't need to upload them here.

### Step 5.4: Test Budget Generation

Start a new conversation in the Project and try:

```
I need a budget range for a main bathroom renovation. About 60 square feet, full gut, keeping plumbing in current locations, converting tub to walk-in shower. Mid-range finishes.
```

Claude should:
- Read your prices from SharePoint
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
- Read your brand guide from SharePoint
- Reformat the budget following your brand guide
- Include all required sections
- Provide instructions for finalizing the PDF

---

## Phase 6: The Automated "Update Catalogue" Workflow

This is the key workflow that makes maintenance effortless. After completing any project, you simply drop your documents into Claude—no copying, no pasting, no manual data entry.

### How It Works

1. **Complete a project** and gather your final documents (budget, invoices, cost breakdown)
2. **Open your Claude Project** (the Budget Generator)
3. **Upload your files** (PDFs, spreadsheets, or images of invoices)
4. **Say "update catalogue"**
5. **Claude extracts the data**, compares to your current prices, and shows you a summary
6. **Confirm the update**
7. **Claude writes directly to SharePoint**—done!

### Example Session

**You:** [Upload: FinalBudget_123MainSt.pdf, Invoices_123MainSt.xlsx]

**You:** Update catalogue

**Claude:** I'll extract the costs from these documents and update your pricing catalogue. First, let me confirm the project details:

- **Project type:** What type of project was this? (bathroom, kitchen, addition, etc.)
- **Square footage:** What was the project area?
- **Quality tier:** Was this Budget, Mid-Range, or Luxury?
- **Completion date:** When was this completed?

**You:** Bathroom renovation, 55 sq ft, mid-range, completed July 2025

**Claude:** I've extracted 23 line items from your documents. Let me read your current catalogue from SharePoint and compare...

Here's what I found:

| Item | Current Mid-Range | New Price | Variance | Action |
|------|-------------------|-----------|----------|--------|
| Demolition - bathroom | $12.00/sq ft | $12.50/sq ft | +4% | Update |
| Tile - floor porcelain | $16.50/sq ft | $18.75/sq ft | +14% | Update |
| Tile - wall subway | $18.00/sq ft | $22.00/sq ft | +22% | **VARIANCE** |
| Heated floor mat | — | $15.00/sq ft | NEW | Add |
| ... | ... | ... | ... | ... |

**Summary:** 18 items to update, 3 new items to add, 2 items with significant variance (>20%)

The wall tile variance is notable—this project was 22% higher than your catalogue. This could be due to material cost increases or project-specific factors.

Should I proceed with updating the catalogue?

**You:** Yes, update it

**Claude:** Catalogue updated successfully:
- 18 items updated with new pricing
- 3 new items added
- All changes are now live in SharePoint at [path]/pricing-catalogue.xlsx
- Last Updated set to July 2025
- Source set to "123 Main St bathroom"

Your next budget will automatically use these updated prices.

---

## Maintaining Your System

### After Every Completed Project (Under 1 minute)

1. Upload your project documents to Claude
2. Say "update catalogue"
3. Review the summary and confirm
4. Done—SharePoint is updated automatically

### Monthly Quick Check (15 minutes)

Ask Claude:
```
Review my pricing catalogue and flag any items where:
- Last Updated is older than 6 months
- Notes say "ESTIMATE - verify"
- We have significant price variance history
```

### Quarterly Review (30 minutes)

```
Compare my catalogue prices to typical current market rates and flag anything that looks outdated. Also identify any common items that are missing from my catalogue.
```

Then update with fresh supplier quotes as needed.

### When Branding Changes

1. Update your brand guide document
2. Save the updated version to SharePoint
3. Test with a PDF export to verify

---

## Troubleshooting

### Claude gives prices that seem wrong
- Ask Claude to read the catalogue and show you the specific item
- Check if the item name matches exactly
- Verify the unit of measure is correct

### Claude says it can't find an item
```
Add [ITEM] to my catalogue with these prices:
- Budget: $X
- Mid-Range: $Y
- Luxury: $Z
- Unit: [per sq ft / each / etc.]
```

### Claude can't connect to SharePoint
- Verify your SharePoint connector is configured correctly
- Check that the file path in your project instructions is correct
- Try: "Can you read the file at [SHAREPOINT PATH]/pricing-catalogue.xlsx?"

### "Update catalogue" isn't extracting costs correctly
- Make sure you're uploading complete documents (not just summaries)
- PDFs with clear tables work best
- For handwritten or unclear invoices, you may need to type key figures

### Budgets are consistently too high/low
```
Compare my last 5 completed projects' actual costs to the budgets I generated for them. Identify which categories are consistently over or under.
```

### Team members get different results
- Make sure everyone is using the same Project
- All team members will access the same SharePoint catalogue automatically

---

## Quick Reference: Key Commands

### Update catalogue after a completed project:
```
[Upload project documents]
Update catalogue
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

### Check catalogue health:
```
Review my pricing catalogue and summarize:
- How many items total
- How many updated in the last 3 months
- Any items marked as estimates that need verification
- Any categories with sparse data
```

### Add a new item manually:
```
Add to my catalogue:
Item: [NAME]
Category: [CATEGORY]
Unit: [UNIT]
Budget: $[X]
Mid-Range: $[Y]
Luxury: $[Z]
Source: [WHERE THIS PRICE CAME FROM]
```

### Compare actual to estimated:
```
Here are the actual costs from a completed project. Compare to what the catalogue would have estimated and flag any significant differences:

[PASTE OR UPLOAD ACTUAL COSTS]
```

---

## Summary: Your Workflow

### Build Once (3-4 hours)
1. Create pricing template from historical projects
2. Set up spreadsheet in SharePoint
3. Process 10-15 projects to populate data
4. Create brand guide and save to SharePoint
5. Set up Claude Project with SharePoint paths and the Update Catalogue skill
6. Upload your logo

### Use Daily
- Generate budgets using your real data (Claude reads from SharePoint)
- Export client-ready PDFs with your branding

### After Each Project (Under 1 minute)
1. Upload project documents to Claude
2. Say "update catalogue"
3. Review and confirm
4. SharePoint updates automatically

### Quarterly (30 minutes)
- Review prices against current supplier quotes
- Clean up estimates and sparse data
- Update brand guide if needed

---

The more projects you process, the more accurate your budgets become. With the SharePoint connector, this improvement happens automatically—just drop your documents and confirm. Your pricing catalogue stays current with zero manual data entry.
