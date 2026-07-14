# Build Your Own Budget Generator: Step-by-Step Walkthrough

This guide walks you through creating your own AI-powered Budget Generator using your actual project data—including branded PDF export for client-ready estimates.

---

## Overview

**What you're building:** A Claude Project that generates accurate budget ranges for new projects based on your historical pricing data, with the ability to export branded PDF estimates.

**Time required:**
- Initial setup: 3-4 hours
- Per project data entry: 15-30 minutes
- Ongoing maintenance: 15 minutes per completed project

**What you'll need:**
- Access to Claude (claude.ai)
- 10-15 completed project files (budgets, invoices, cost breakdowns)
- A spreadsheet program (Excel or Google Sheets)
- Your company's brand assets (logo, colors, fonts)

---

## Phase 1: Create Your Pricing Spreadsheet Template

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

### Step 1.4: Download and Set Up Your Spreadsheet

1. Copy Claude's CSV output
2. Open Excel or Google Sheets
3. Paste the content (use "Paste Special > Text" if formatting looks wrong)
4. Save as `[YourCompany]-pricing-catalogue.csv`

You now have an empty template structured around YOUR actual project categories.

---

## Phase 2: Populate with Historical Data

### Step 2.1: Process Your First Project

Take your first completed project. Open Claude and use this prompt:

```
I'm building a pricing database from historical projects. Here's the cost breakdown from a completed [PROJECT TYPE] project:

[PASTE BUDGET/INVOICE DETAILS]

Project details:
- Square footage: [X]
- Quality tier: [Budget / Mid-Range / Luxury]
- Completion date: [Month/Year]
- Any unusual factors: [site access issues, custom work, etc.]

Please extract the costs and calculate per-unit pricing where applicable. Format as:
- Category
- Item
- Quantity and unit
- Total cost
- Per-unit cost

Flag any costs that seem unusually high or low.
```

### Step 2.2: Add to Your Spreadsheet

Take Claude's output and add the per-unit costs to your spreadsheet in the appropriate tier column (Budget, Mid-Range, or Luxury based on the project quality level).

**Example:**
- Project was mid-range quality
- Tile installation cost $2,400 for 150 sq ft = $16/sq ft
- Enter $16.00 in the "Mid-Range Price" column for "Tile - Porcelain" or similar item

### Step 2.3: Repeat for Remaining Projects

Process each project the same way:
1. Paste the budget/invoice into Claude
2. Get per-unit costs extracted
3. Add to your spreadsheet in the correct tier column

**As you go, you'll notice:**
- Some items appear in multiple projects (great for averaging)
- Some items only appear once (use as starting point, refine later)
- Price variations between projects (quality tier differences, market changes)

### Step 2.4: Calculate Averages (If You Have Multiple Data Points)

Once you've processed several projects, you may have multiple prices for the same item. Use this prompt:

```
I have these data points for interior painting costs:
- Project A (mid-range): $3.80/sq ft
- Project B (mid-range): $4.20/sq ft
- Project C (budget): $2.60/sq ft
- Project D (luxury): $6.50/sq ft

Help me establish reasonable pricing tiers:
- Budget price
- Mid-Range price
- Luxury price

Consider that some variation is normal. Flag any outliers I should investigate.
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

**Important:** Always verify Claude's estimates against real quotes. Mark estimated prices in your Notes column so you know to update them when you get real data.

---

## Phase 4: Create Your Brand Guide

Your Brand Guide tells Claude how to format client-facing documents. This ensures every PDF estimate looks professional and consistent with your company's identity.

### Step 4.1: Gather Your Brand Assets

Collect:
- Your logo file
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
2. Include all required sections (cover, summary, breakdown, notes, terms, contact)
3. Use brand colors, fonts, and tone of voice
4. Include the standard disclaimer
5. Provide instructions for finalizing the PDF

## Standard Additions
- Permits: 1.5% of construction value
- Project Management: 8% (Budget), 10% (Mid-Range), 12% (Luxury)
- Contingency: 10% (Budget), 15% (Mid-Range), 20% (Luxury)

## Important
- Round to reasonable precision (not $1,847.23—use $1,850)
- These are estimates for budgeting, not formal quotes
- Remind users that actual costs depend on site conditions and final selections
- Always follow the Brand Guide for tone, language, and formatting
```

### Step 5.3: Upload Your Project Files

Click **Add content** or the **+** button and upload both files:

| File | Purpose |
|------|---------|
| `[YourCompany]-pricing-catalogue.csv` | Your pricing data |
| `[YourCompany]-brand-guide.md` | Your brand standards for PDF export |

Claude now has access to both files in every conversation within this Project.

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

## Phase 6: Maintain Your Project

### After Every Completed Project

1. **Pull the final costs** from the completed project
2. **Calculate per-unit prices** for each category
3. **Compare to your catalogue:**
   - If similar: Your data is accurate
   - If different: Update the catalogue or investigate why
4. **Add any new items** that weren't in your catalogue
5. **Re-upload** the updated CSV to your Claude Project

### Quarterly Review

- Compare catalogue prices to current supplier quotes
- Adjust for material price changes
- Archive items you no longer use
- Add items for new services you're offering

### Updating Your Brand

If your branding changes (new colors, updated tagline, new awards):
1. Update your brand guide document
2. Re-upload to the Claude Project
3. Test with a PDF export to verify changes

### Keep Notes

In the Notes column of your pricing catalogue, track:
- When prices were last verified
- Source of the price (which project, or supplier quote)
- Any special conditions (e.g., "assumes easy access")

---

## Troubleshooting

### Claude gives prices that seem wrong
- Check if the item exists in your catalogue (exact name match matters)
- Verify the unit of measure is correct
- Update the catalogue if prices have changed

### Claude says it can't find an item
- Add the item to your catalogue
- Or try different wording (Claude matches on the item name in your CSV)

### Budgets are consistently too high/low
- Compare recent actuals to catalogue prices
- Your contingency percentages may need adjustment
- Some categories may have outdated pricing

### Team members get different results
- Make sure everyone is using the same Project (not regular Claude chat)
- Verify everyone has the latest version of the catalogue uploaded

### PDF formatting looks off
- Check that your brand guide is uploaded to the Project
- Review the brand guide for any formatting issues
- Try re-uploading the brand guide file

### PDF missing sections
- Make sure the PDF export instructions are in your project instructions
- Use clear trigger phrases like "export as PDF" or "make this client-ready"

---

## Quick Reference: Prompts to Save

### Extract costs from a completed project:
```
Extract per-unit costs from this project. Format as Category, Item, Quantity, Unit, Total Cost, Per-Unit Cost. Flag anything unusual.

[PASTE PROJECT DATA]
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
Here are actual costs from a completed project. Compare to the catalogue and flag any significant differences (>15%):

[PASTE ACTUAL COSTS]
```

### Add a new item:
```
I need to add [ITEM] to my catalogue. Based on these similar items in my data, suggest reasonable Budget/Mid/Luxury tiers:

[LIST SIMILAR ITEMS AND THEIR PRICES]
```

### Update brand guide:
```
I need to update my brand guide. Please add:
- New award: [AWARD NAME AND YEAR]
- Updated tagline: [NEW TAGLINE]

Keep everything else the same.
```

---

## Summary: Your Workflow

1. **Build once:**
   - Create pricing template → Process 10-15 projects
   - Create brand guide
   - Set up Claude Project with both files

2. **Use daily:**
   - Generate budgets from the Project using your real data
   - Export client-ready PDFs with your branding

3. **Maintain ongoing:**
   - Add each completed project's data
   - Quarterly price reviews
   - Update brand guide as needed

The more projects you add, the more accurate your budgets become. The more you refine your brand guide, the more polished your client documents become.
