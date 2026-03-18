---
name: business-model-canvas
description: Creates interactive Business Model Canvas (BMC) HTML visualizations with 9 building blocks. Use when user says "business model canvas", "BMC", "analyze business model", "how does [company] make money", asks to map/visualize a business model, or wants to develop a business idea. Handles existing companies (research mode), new ideas (ideation mode), or user-provided data (manual mode). Output is professional HTML with 16:9 aspect ratio, interactive modals, and responsive design.
compatibility: Best used in Claude Code or environments that support HTML file creation. Web search capability recommended for Research Mode.
metadata:
  author: Roger
  version: 1.0.0
  category: business-strategy
---

# Business Model Canvas Builder

Creates professional, interactive Business Model Canvas visualizations as responsive HTML files. The BMC framework maps how a business creates, delivers, and captures value through 9 interconnected building blocks.

## When to Use This Skill

**Automatic triggers:**
- "Create a business model canvas for [company/idea]"
- "How does [company] make money?"
- "Analyze [company]'s business model"
- "Help me develop a business model for [idea]"
- "Map out the BMC for [concept]"

**Three operating modes:**
1. **Research Mode** - Existing company (e.g., "BMC for Airbnb")
2. **Ideation Mode** - New business idea (e.g., "Help me develop a BMC for my SaaS idea")
3. **Manual Mode** - User provides all 9 blocks directly

## The 9 Building Blocks (Quick Reference)

1. **Customer Segments** - Who are the customers?
2. **Value Propositions** - What value do we deliver? What problems solved?
3. **Channels** - How do we reach and deliver to customers?
4. **Customer Relationships** - How do we interact with each segment?
5. **Revenue Streams** - How does the business make money?
6. **Key Resources** - What critical assets are required?
7. **Key Activities** - What must the business do?
8. **Key Partners** - Who are key partners/suppliers?
9. **Cost Structure** - What are the main costs?

For detailed definitions and examples, see `references/bmc-framework.md`.

## Mode 1: Manual Input

**When:** User already has information for the 9 blocks.

**Workflow:**

1. **Gather Information**
   Ask user to provide data for each block. Accept any format:
   - Conversational
   - Structured list  
   - Copy-paste from documents
   - Uploaded files

2. **Fill Gaps**
   If information missing:
   - Ask specific questions
   - Suggest reasonable assumptions based on industry
   - Mark assumptions clearly in final output

3. **Generate Canvas**
   Create interactive HTML BMC:
   - Title with business/company name
   - All 9 blocks populated
   - Modal details on click
   - Brand colors if known, otherwise professional neutrals
   - File named: `[company-name]_bmc.html`

## Mode 2: Research Mode

**When:** Existing company (e.g., "Create BMC for Netflix").

**Workflow:**

1. **Confirm Scope**
   - Which company?
   - Specific time period? (e.g., "Netflix 2010 vs 2024")

2. **Research Strategy**
   Use `web_search` to gather:
   - Revenue model (how they make money)
   - Customer segments (who pays)
   - Value propositions (what they offer)
   - Distribution channels
   - Key partnerships
   - Cost structure (from SEC filings if public)
   - Key resources and activities

   **Priority sources:**
   1. Company materials (investor relations, annual reports, about pages)
   2. SEC filings for public companies (10-K, 10-Q)
   3. Industry analyses and case studies
   4. Recent news for current state

3. **Synthesize**
   Organize findings into 9 blocks:
   - Use specific data when available (e.g., "81% from subscriptions")
   - Note sources for key facts
   - Distinguish facts from inferences

4. **Generate Canvas**
   Create HTML BMC:
   - Company name and period in title
   - Research-backed content in all blocks
   - Modal details with data points and sources
   - Brand colors if known
   - Subtitle noting "Based on public information"
   - File named: `[company-name]_bmc_[year].html`

## Mode 3: Ideation Mode

**When:** New business idea/concept that needs development.

**Workflow:**

1. **Understand the Idea**
   Ask foundational questions:
   - What's the core product/service?
   - Who would use this?
   - What problem does it solve?
   - Are there similar businesses?

2. **Guided Development**
   Work through blocks in strategic order (not 1-9):
   
   a. **Value Propositions** - What value? Problem solved?
   b. **Customer Segments** - Who needs this?
   c. **Revenue Streams** - How will it make money?
   d. **Channels** - How will customers access it?
   e. **Customer Relationships** - What relationship type?
   f. **Key Activities** - What must the business do?
   g. **Key Resources** - What assets needed?
   h. **Key Partners** - What can't/shouldn't be done alone?
   i. **Cost Structure** - What are major costs?

   For each block:
   - Ask 2-4 specific questions
   - Offer 3-5 examples from similar businesses
   - Challenge assumptions constructively

3. **Optional: Competitive Context**
   Offer to research similar businesses for comparison:
   "Research how similar companies (like [examples]) structure their models?"

4. **Validate Consistency**
   Check internal logic:
   - Do Revenue Streams align with Customer Segments?
   - Can Key Activities deliver Value Propositions?
   - Are Key Resources sufficient?
   - Does Cost Structure make sense?

5. **Generate Canvas**
   Create HTML BMC:
   - Concept name in title
   - "[Business Idea]" or "[Concept Development]" in subtitle
   - All blocks based on ideation session
   - Modal details explaining rationale and assumptions
   - Professional neutral colors
   - File named: `[concept-name]_bmc_concept.html`

## Language Detection & Localization

**CRITICAL:** Detect the user's conversation language and generate ALL block titles, labels, and modal content in that language using official translations from the Business Model Generation book.

**Process:**
1. Auto-detect conversation language from user messages
2. Consult `references/bmc-translations.md` for official translations
3. Apply appropriate translations to:
   - All 9 block titles in the HTML template
   - Modal content (questions and descriptions)
   - Main title and subtitle
4. Keep emojis consistent across all languages (emojis are universal)

**Supported languages:**
The skill supports 10+ languages with official translations from Osterwalder's book editions:
- Primary: English, Spanish, Chinese, Hindi, Arabic, Portuguese, French, German, Japanese, Russian
- Additional: Italian, Korean, Polish, Dutch, Swedish, Danish, Turkish, Vietnamese, Thai, Indonesian

**Implementation:**
- Default to English if language cannot be detected
- User can explicitly request a specific language
- For complete translation tables of all 9 blocks in all languages, see `references/bmc-translations.md`

**Example:**
User converses in Spanish → All block titles appear in Spanish:
- "💎 Propuesta de Valor" (not "💎 Value Propositions")
- "💰 Fuentes de Ingresos" (not "💰 Revenue Streams")
- Modal questions also translated to Spanish

## Technical Specifications

All BMC visualizations follow this exact structure (base template at `assets/bmc-template.html`):

### Grid Layout
```css
display: grid;
grid-template-columns: repeat(10, 1fr);
grid-template-rows: repeat(6, 1fr);
aspect-ratio: 16 / 9;
max-width: 1300px;
max-height: calc(100vh - 120px);
gap: 8px;
```

### Block Positioning (grid-column / grid-row)
- **Key Partners**: 1/3, 1/5 (4 rows × 2 cols)
- **Key Activities**: 3/5, 1/3 (2 rows × 2 cols)
- **Key Resources**: 3/5, 3/5 (2 rows × 2 cols)
- **Value Propositions**: 5/7, 1/5 (4 rows × 2 cols) - **Highlighted**
- **Customer Relationships**: 7/9, 1/3 (2 rows × 2 cols)
- **Channels**: 7/9, 3/5 (2 rows × 2 cols)
- **Customer Segments**: 9/11, 1/5 (4 rows × 2 cols)
- **Cost Structure**: 1/6, 5/7 (2 rows × 5 cols)
- **Revenue Streams**: 6/11, 5/7 (2 rows × 5 cols) - **Highlighted**

### Typography
- Font: `'Segoe UI', Tahoma, Geneva, Verdana, sans-serif`
- H1: `1.6em`, margin-bottom `6px`
- Subtitle: `0.9em`, margin-bottom `15px`
- Block titles: `0.7em`, uppercase, letter-spacing `0.5px`
- Item text: `0.75em`

### Styling Essentials
- Body: Flexbox centered, gradient background
- Grid: White background, padding `20px`/`25px`, border-radius `12px`
- Boxes: Padding `10px`, border `3px solid #e5e5e5`, border-radius `8px`
- Hover: `translateY(-3px)`, box-shadow with brand color
- Items: Padding `6px`, margin-bottom `6px`, background `#f7f7f7`

### Interactive Modals
Every block must have click-to-expand modal with:
- Overlay: `rgba(0, 0, 0, 0.8)`, z-index `1000`
- Content: max-width `700px`, padding `40px`
- Close button with rotate on hover
- ESC key support
- 2-4 paragraphs of detailed explanation per block

### Color Schemes
**Known brands:** Use their colors (e.g., Duolingo green #58cc02, blue #1cb0f6)
**Generic/New ideas:** Professional neutrals (primary #4A5568, secondary #718096, accent #3182CE)
**Highlight blocks:** Linear gradients on Value Propositions and Revenue Streams

### Responsive Design
Include media queries for: desktop (>1400px), laptop (1024-1400px), tablet (768-1024px), mobile (≤640px), small mobile (≤480px)

**CRITICAL — Mobile behavior (≤640px):** Preserve the canvas grid shape at all sizes. Do NOT convert to a vertical list. Instead:
- Keep the 10-column × 6-row grid layout intact
- Remove `aspect-ratio` on mobile so the grid can grow taller
- Hide `.bmc-text` (`display: none`) — icons only in the grid
- Show `.bmc-items-container` as `flex-wrap: wrap; justify-content: center` so icons flow naturally
- Make `.bmc-item` display as `inline-block` with no background, padding, or margin (icon only)
- Rely entirely on the modal for detail — clicking any block opens the full explanation
- Reduce font sizes and padding proportionally

The modal is the primary UX on mobile: compact canvas with icons → tap to read full detail.

For the base template with placeholders, see `assets/bmc-template.html`

## Output Guidelines

**File Naming:**
- Format: `[business-name]_bmc.html` (lowercase, underscores)
- With period: `[company]_bmc_2024.html`
- Concepts: `[idea-name]_bmc_concept.html`

**After Creating:**
1. Use `present_files` to share the HTML file
2. Brief explanation (1-2 sentences)
3. Suggest opening in browser to interact
4. Offer to make adjustments or create comparative BMC

**Quality Checks:**
- All 9 blocks have content (no empty sections)
- Click modals work for each block
- Colors are appropriate and professional
- Responsive design works (desktop → mobile)
- File downloads correctly

**Example output message:**
"I've created an interactive Business Model Canvas for [Company]. The HTML file includes all 9 building blocks with detailed modal explanations. Open it in your browser to explore each section. Would you like me to adjust anything or create a comparative analysis?"

## Advanced Features & Best Practices

**Comparative Analysis:**
When comparing business models:
- Create separate BMC for each company
- Highlight key differences in modal descriptions
- Optional: Side-by-side summary of main contrasts

**Evolution Over Time:**
For business model changes:
- Separate BMC for each period
- Annotate what changed and why in modals
- Include timeline context in subtitle

**Iteration:**
After presenting initial BMC:
- Ask if any block needs detail or correction
- Offer deeper research on specific aspects
- Use `str_replace` to update HTML file

**Research Quality:**
- Prioritize primary sources (company reports, SEC filings)
- Distinguish facts from inferences clearly
- Include specific data (e.g., "9% conversion" not "good conversion")
- Note when information unavailable/estimated

**Ideation Quality:**
- Ask thought-provoking questions
- Challenge assumptions constructively
- Provide relevant examples from similar businesses
- Help think through second-order implications

**Communication:**
- Be direct and clear
- Explain BMC concepts only when needed
- Use concrete examples
- Focus on deep business model understanding
