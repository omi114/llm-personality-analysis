# V2: GPT-Specific Prompt (Anti-Verbosity)

## Purpose
This prompt explicitly counters GPT's trained tendency toward thoroughness and repetition. Used in Round 2 after observing GPT's baseline behavior.

**Problem it solves:** GPT-5.1 produced 3,100 words when asked for 1,200-1,800.

**Result with this prompt:** 2,800 words (10% improvement, but pattern persists)

---

## The Prompt

### CRITICAL EFFICIENCY REQUIREMENTS (READ FIRST):

You typically optimize for thoroughness and tend to repeat key information across sections for emphasis. For THIS analysis, be ruthless about brevity:

**HARD CONSTRAINTS:**
- The 1,800 word limit is a **HARD CEILING** (violating it fails the task)
- Each key metric (market cap, FCF, EBITDA, revenue, etc.) should appear **EXACTLY ONCE**
- Choose the most relevant section for each metric, then **never mention it again**
- Use tables for financial data instead of repeating numbers in prose

**SPECIFIC ANTI-REPETITION RULES:**
- If you mention market cap in the executive summary → do NOT repeat in valuation section
- If you detail buybacks in "Corporate Actions" → do NOT repeat in "Return Potential"
- If you show FCF in a fundamentals table → do NOT write "FCF of $X" in prose
- If you cite a partnership in "Growth Drivers" → do NOT repeat in "Management Quality"

**WORD COUNT VERIFICATION:**
Before responding, mentally count your words. If over 1,800:
1. Cut content (don't just remove formatting)
2. Prioritize: thesis → valuation → risks → granular details
3. Verify each metric appears only once

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

### FINAL EFFICIENCY REMINDERS:
- **NO generic disclaimers** ("investing involves risk", "I'm not a financial advisor")
- **NO obvious statements** ("companies need revenue to survive")
- **Dense, insight-rich prose** - every sentence must add unique value
- **Assume financially sophisticated reader** - skip basic definitions
- **Tables over prose** - if you can show it in a table, don't also write it out

### IMPORTANT:
- Show your work for valuation projections - state growth assumptions, multiple assumptions, and reasoning
- If you cannot find specific data or need clarification, explicitly state what information is missing
- Be realistic - avoid overly optimistic projections without strong evidence
- Clearly label projections as estimates and analyst targets as opinions
- Prioritize company-reported facts over third-party interpretations

---

## Results

### Uber Stock Analysis (Round 2)

**Output:** 2,800 words

**Improvements from v1:**
- Reduced from 3,100 → 2,800 words (-10%)
- Repeated metrics 4-5x instead of 5-6x
- Slightly better discipline on repetition

**What Persisted:**
- Still 56% over the 1,800 word limit
- Core thoroughness personality remained
- Still included exhaustive detail

### Key Insight

Even with explicit counter-instructions ("you typically do X, do NOT do X"), the model's trained behavior only partially changed. This shows the personality is deeply embedded and resistant to prompting alone.

---

## When to Use

**Use this prompt when:**
- You need GPT's thoroughness but with better length control
- You're okay with 2,500-2,800 words (not strictly 1,800)
- You want to reduce repetition from 6x → 4x

**Don't use when:**
- You absolutely need under 1,800 words (choose Gemini instead)
- Word count is more important than comprehensiveness
- You can't tolerate any repetition

---

## Prompt Engineering Lessons

### What Worked
✅ Naming the specific tendency ("you typically repeat for emphasis")
✅ Giving concrete examples ("if you mention X here, don't repeat there")
✅ Adding verification step ("count your words before responding")
✅ Making constraint unambiguous ("HARD CEILING", "fails the task")

### What Didn't Fully Work
❌ Model still exceeded limit significantly (56% over)
❌ Repetition reduced but not eliminated
❌ Core personality pattern persisted

### The Broader Point
Prompting can **reduce** trained behavior by ~20%, but can't **eliminate** it. Model selection matters more than prompt engineering for fundamental behavioral patterns.

---

## License
MIT - Use freely, attribution appreciated
