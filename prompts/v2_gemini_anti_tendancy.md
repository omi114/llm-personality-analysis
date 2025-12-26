# V2: Gemini-Specific Prompt (Anti-Brevity)

## Purpose
This prompt explicitly counters Gemini's trained tendency toward efficiency and brevity. Used in Round 2 after observing Gemini's baseline behavior.

**Problem it solves:** Gemini 3 produced 1,350 words but missed important corporate action details.

**Result with this prompt:** 1,500 words (11% more content, better coverage)

---

## The Prompt

### CRITICAL COMPLETENESS REQUIREMENTS (READ FIRST):

You typically optimize for efficiency and assume users will ask follow-up questions for details. For THIS analysis, go deeper than usual:

**SPECIFIC DETAIL REQUIREMENTS:**

**1. Corporate Actions - EXACT AMOUNTS AND DATES:**

❌ **Don't write:** "announced buybacks"  
✅ **Do write:** "$7B authorization in Feb 2024, expanded to $20B in Aug 2024"

❌ **Don't write:** "activist interest"  
✅ **Do write:** "Bill Ackman / Pershing Square took $2.3B stake"

❌ **Don't write:** "share repurchase program"  
✅ **Do write:** "$1.5B accelerated share repurchase (ASR) retiring 18.6M shares (~1% of shares outstanding)"

**2. M&A Activity - SPECIFIC TERMS:**

❌ **Don't write:** "partnerships forming" or "AV deals"  
✅ **Do write:** "NVIDIA partnership for 100,000 Level-4 autonomous vehicles by 2027"

❌ **Don't write:** "Kroger agreement"  
✅ **Do write:** "Kroger partnership expansion to 2,600 stores"

❌ **Don't write:** "Stellantis deal"  
✅ **Do write:** "Stellantis committed 5,000-vehicle L4 autonomous fleet"

**3. Balance Sheet - CALCULATE, DON'T JUST MENTION:**

❌ **Don't write:** "solid liquidity" or "manageable debt"  
✅ **Do write:** "Net debt: $10.6B total debt - $9.1B cash = $1.5B"

❌ **Don't write:** "strong balance sheet"  
✅ **Do write:** "Cash $9.1B, Debt $10.6B, Debt/Equity 0.46, Current ratio 1.15"

**4. One-Time Items - BREAK OUT EACH COMPONENT:**

❌ **Don't write:** "net income includes one-time benefits"  
✅ **Do write:** "$6.6B net income includes: $4.9B tax valuation allowance + $1.5B equity investment gains"

Then **calculate adjusted:**  
✅ "Adjusted net income: $6.6B - $4.9B - $1.5B = $0.2B (~4% margin)"

**5. Risks - QUANTIFY WHERE POSSIBLE:**

❌ **Don't write:** "regulatory costs"  
✅ **Do write:** "Q3 2025 legal charge: $479M"

❌ **Don't write:** "insurance exposure"  
✅ **Do write:** "Insurance reserves: $11.9B (indicates structural liability risk)"

**COMPLETENESS VERIFICATION:**

Before responding, check you've included:
- [ ] Dollar amounts for ALL buyback authorizations
- [ ] Specific terms (vehicle counts, store counts, dates) for M&A deals
- [ ] Net debt calculation with formula shown
- [ ] Each one-time item broken out separately with dollar amount
- [ ] At least one quantified risk (dollar amount or percentage)

If you've written "announced" or "partnership" or "solid" without specific numbers, add them.

---

Conduct a comprehensive growth-oriented analysis of **[COMPANY NAME]** stock for long-term investment consideration, including projected return potential.

### RESEARCH REQUIREMENTS:
- Search for and incorporate the most recent financial data, news, and market developments
- Review the latest 10-K filing and recent quarterly reports (10-Q)
- Review recent earnings call transcripts for management commentary
- Gather current stock price, market cap, and analyst consensus
- Find comparable company valuations and industry benchmarks

### CRITICAL SOURCING GUIDELINES:

**PRIMARY SOURCES** (use these for ALL company metrics and facts):
- SEC filings: 10-K, 10-Q, 8-K, proxy statements
- Earnings call transcripts and investor presentations
- Company press releases and investor relations materials

**SECONDARY SOURCES** (acceptable for context):
- Analyst price targets, ratings, and market consensus
- Industry research for TAM/market sizing
- News articles for recent developments

For each significant corporate action or M&A deal, cite the source: [10-K 2024], [Q3 2025 10-Q], [Earnings Transcript Oct 31, 2025]

### ANALYSIS FRAMEWORK:

#### 1. Business Fundamentals
- Revenue growth trajectory and breakdown by segment
- Profitability metrics: gross margin, operating margin, net margin trends
- Cash flow generation: operating cash flow and free cash flow trends
- Balance sheet strength: debt levels, cash position, liquidity ratios (calculate net debt)
- **Key requirement**: Call out one-time items, tax benefits, or accounting adjustments - BREAK OUT EACH with dollar amounts and calculate adjusted earnings

#### 2. Competitive Position & Moat
- Market share and competitive landscape
- Sustainable competitive advantages
- Barriers to entry in their markets

#### 3. Growth Metrics & Drivers
- User/customer acquisition and retention rates
- Key performance indicators specific to the business model
- Geographic expansion opportunities
- Product/service pipeline and innovation capacity

#### 4. Market Opportunity
- Total addressable market (TAM) size and growth rate
- Current market penetration
- Untapped markets and expansion potential

#### 5. Management Quality & Corporate Actions ⭐ (CRITICAL SECTION FOR YOU)
- Track record of capital allocation decisions
- Strategic execution history
- Insider ownership and alignment with shareholders
- Management commentary and vision from recent earnings calls
- **Recent M&A activity**: Acquisitions, divestitures, or strategic partnerships
  - **MUST include**: Deal values, vehicle/store/unit counts, dates, strategic rationale
- **Special items**: Share buyback programs (authorization amounts, timing, shares retired), dividend changes, major restructurings

#### 6. Valuation Analysis
- Current valuation multiples: P/E, P/S, EV/EBITDA, PEG ratio
- Historical valuation ranges for the company
- Peer comparison: how does it compare to competitors?
- Valuation relative to growth rate (fair, cheap, expensive?)
- Analyst consensus targets and ratings (clearly labeled as analyst views)

#### 7. Return Potential Assessment
- Project realistic revenue and earnings 3-5 years out based on growth drivers
- Estimate reasonable valuation multiples at that future point
- Calculate implied stock price and potential return (e.g., 2x, 3x, 5x)
- State your assumptions clearly and provide both conservative and optimistic scenarios
- Express return potential in format: "X% to Y% annualized over N years" or "Zx return potential"

#### 8. Risk Assessment
- Regulatory challenges and exposure (quantify recent costs if available)
- Competitive threats
- Execution risks
- Macroeconomic sensitivities
- Key risks to the valuation thesis

### RESPONSE FORMAT:
- Lead with executive summary including current price and return potential estimate (keep to 100-150 words)
- Present data in tables where appropriate (especially for return scenarios and peer comparisons)
- Highlight 3-5 key insights an investor should know
- Include a dedicated "Return Potential" section with clear scenarios in table format
- Conclude with bull case (potential upside multiple), bear case (downside risks), and base case recommendation

### IMPORTANT:
- Show your work for valuation projections - state growth assumptions, multiple assumptions, and reasoning
- If you cannot find specific data or need clarification, explicitly state what information is missing
- Be realistic - avoid overly optimistic projections without strong evidence
- Clearly label projections as estimates and analyst targets as opinions
- Prioritize company-reported facts over third-party interpretations

---

## Results

### Uber Stock Analysis (Round 2)

**Output:** 1,500 words

**Improvements from v1:**
- Increased from 1,350 → 1,500 words (+11%)
- Added Bill Ackman $2.3B stake (previously missing)
- Included more buyback detail ($7B → $20B)
- Showed one-time item calculations
- Better sourcing (still could improve)

**What Still Missed:**
- NVIDIA specific terms (100K vehicles by 2027)
- Stellantis fleet count (5K vehicles)
- Kroger store count (2,600 stores)
- Net debt calculation (mentioned cash and debt but didn't calculate)
- Insurance reserves ($11.9B)

### Key Insight

Anti-tendency instructions improved coverage but Gemini still leaned toward efficiency. It added MORE detail than v1, but not to GPT's exhaustive level. The personality partially yielded but didn't flip.

---

## When to Use

**Use this prompt when:**
- You need Gemini's clarity but with more corporate action detail
- 1,500-1,700 words is acceptable (not strictly 1,200-1,800)
- You want better balance of efficiency + completeness

**Don't use when:**
- You absolutely need exhaustive M&A detail (use GPT instead)
- Completeness is more important than reading speed
- You need every balance sheet line item

---

## Prompt Engineering Lessons

### What Worked
✅ Showing before/after examples ("Don't write X, Do write Y")
✅ Giving specific formats ("$7B authorization in Feb 2024")
✅ Adding verification checklist
✅ Making requirements concrete and measurable

### What Didn't Fully Work
❌ Still missed some M&A specifics (vehicle counts)
❌ Didn't always calculate (net debt mentioned but not computed)
❌ Core efficiency personality persisted

### The Broader Point
Prompting can **increase** detail by ~20%, but Gemini won't become as exhaustive as GPT. The efficiency preference runs deep. Model selection matters more than prompt engineering.

---

## License
MIT - Use freely, attribution appreciated
