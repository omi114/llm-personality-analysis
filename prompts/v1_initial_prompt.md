# V1: Initial Prompt (Generic Instructions)

## Purpose
This is the baseline prompt used in Round 1 of testing. It contains standard instructions for comprehensive analysis without model-specific adaptations.

**Problem:** Both models applied their trained priors to ambiguous instructions like "comprehensive" and "1,800 words," resulting in 2.3x length difference.

---

## The Prompt

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

### ANALYSIS FRAMEWORK:

#### 1. Business Fundamentals
- Revenue growth trajectory and breakdown by segment
- Profitability metrics: gross margin, operating margin, net margin trends
- Cash flow generation: operating cash flow and free cash flow trends
- Balance sheet strength: debt levels, cash position, liquidity ratios
- **Key requirement**: Call out one-time items, tax benefits, or accounting adjustments that distort reported earnings

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

#### 5. Management Quality & Corporate Actions
- Track record of capital allocation decisions
- Strategic execution history
- Insider ownership and alignment with shareholders
- Management commentary and vision from recent earnings calls
- **Recent M&A activity**: Acquisitions, divestitures, or strategic partnerships (with deal values/timing where available)
- **Special items**: Share buyback programs, dividend changes, major restructurings

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
- Regulatory challenges and exposure
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

### CRITICAL EFFICIENCY REQUIREMENTS:
- Target 1,200-1,800 words total (no more than 2,000 words)
- Every sentence should add unique value - avoid repetition
- Use tables for financial data instead of repeating numbers in prose
- If you mention a key metric (like FCF or market cap), mention it ONCE in the most relevant section
- No generic disclaimers or obvious statements ("investing involves risk", "past performance doesn't guarantee future results")
- Dense, insight-rich prose similar to a professional equity research report
- Assume the reader is financially sophisticated - skip basic definitions

### IMPORTANT:
- Show your work for valuation projections - state growth assumptions, multiple assumptions, and reasoning
- If you cannot find specific data or need clarification, explicitly state what information is missing
- Be realistic - avoid overly optimistic projections without strong evidence
- Clearly label projections as estimates and analyst targets as opinions
- Prioritize company-reported facts over third-party interpretations

---

## Results When Used

### Uber Stock Analysis (November 2025)

| Model | Output |
|-------|---------|
| **GPT-5.1** | 3,100 words (72% over limit) |
| **Gemini 3** | 1,350 words (within bounds) |
| **Gap** | 2.3x length difference |

### What Happened

**GPT-5.1:**
- Interpreted "comprehensive" as primary directive
- Treated "1,800 words" as a guideline, not a hard limit
- Repeated key metrics (market cap, FCF, EBITDA) 5-6 times across sections
- Included exhaustive corporate action detail
- Cited multiple sources (10-K, 10-Q, earnings transcripts)

**Gemini 3:**
- Interpreted "1,800 words max" as primary constraint
- Stayed well under to avoid violation (safety margin)
- Zero repetition (each metric mentioned exactly once)
- Lighter on corporate action details
- One primary source cited (Q3 2025 earnings release)

### Why This Prompt Failed to Constrain

The instructions contained **implicit tension**:
- "Comprehensive" suggests MORE content
- "1,800 words max" suggests LESS content

Without explicit prioritization, each model applied its trained prior:
- GPT: "Comprehensive" wins → include everything
- Gemini: "Word limit" wins → stay efficient

---

## Key Learnings

### What Didn't Work

❌ **"Target 1,200-1,800 words"**
- Too ambiguous
- GPT read as "around 3,000 is fine"
- Gemini read as "stay under 1,500 to be safe"

❌ **"Avoid repetition"**
- Too generic
- GPT repeated anyway (learned behavior: repetition = emphasis = helpful)

❌ **"Dense, insight-rich prose"**
- Open to interpretation
- GPT: "Dense = include every detail"
- Gemini: "Dense = maximum information per word"

### What This Taught Us

Generic constraints don't override trained behavior. Models need:
1. Explicit acknowledgment of their tendency
2. Concrete counter-examples
3. Unambiguous prioritization when instructions conflict

This led to **v2: Anti-Tendency Prompt** →

---

## Next Steps

See:
- [v2 for GPT](v2_gpt_anti_tendency.md) - Anti-verbosity instructions
- [v2 for Gemini](v2_gemini_anti_tendency.md) - Anti-brevity instructions
- [Prompt Evolution Analysis](prompt_evolution.md) - Full comparison

---

## Using This Prompt

**Recommended for:**
- Establishing baseline behavior of a new model
- Understanding a model's natural output style
- Research comparing multiple models' defaults

**Not recommended for:**
- Production systems (use v2 instead)
- When you need specific output length
- When you've already observed the model's tendency
