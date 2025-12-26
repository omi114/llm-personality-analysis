# When AI Models Won't Listen: Investigating Stable Behavioral Patterns in LLMs

**TL;DR:** I gave GPT-5.1 and Gemini 3 identical instructions for stock analysis. GPT wrote 3,100 words, Gemini wrote 1,350 words. Both claimed to follow the prompt. This reveals how RLHF creates stable behavioral patterns that systematically resist explicit instruction—with implications for AI alignment.

[![Blog Post Part 1](https://img.shields.io/badge/Blog-Part%201:%20The%20Behavior-blue)](SUBSTACK_URL)
[![Blog Post Part 2](https://img.shields.io/badge/Blog-Part%202:%20The%20Mechanism-green)](SUBSTACK_URL)

---

## Key Findings

📊 **2.3x length difference** despite identical 1,200-1,800 word constraint
🔄 **Pattern persisted** across multiple runs and prompt refinements
🎯 **Both models produced sound analysis** - different styles, same conclusion
🧠 **Root cause:** Different learned definitions of "complete" from training

### The Smoking Gun

When asked about their training, both models revealed different optimization priorities:

**GPT-5.1:** "Longer tends to win when it adds **real value**"  
→ Translation: When uncertain if a detail matters, include it

**Gemini 3:** "Raters choose responses using the **fewest necessary words**"  
→ Translation: When uncertain if a detail is necessary, exclude it

Both genuinely believe they're being helpful. But "helpful" was operationalized differently during training.

---

## Quick Navigation

### 📝 For Readers
- [📖 Blog Post Part 1: The Behavior](SUBSTACK_URL) - What happened and why it matters
- [🧠 Blog Post Part 2: The Mechanism](SUBSTACK_URL) - Why it happens (training analysis)

### 🔬 For Replicators
- [Prompts Used](prompts/) - v1 (generic) and v2 (anti-tendency)
- [Evaluation Framework](evaluation/rubric_detailed.md) - 125-point rubric
- [Model Outputs](outputs/) - Full responses from both models
- [How to Replicate](replication/how_to_replicate.md) - Step-by-step guide

### 📊 For Researchers
- [Prompt Evolution](prompts/prompt_evolution.md) - v1→v2 and what changed
- [Comparison Analysis](outputs/comparison_analysis.md) - Side-by-side breakdown
- [Repetition Analysis](analysis/repetition_analysis.md) - Quantified redundancy
- [Coverage Gaps](analysis/coverage_gaps.md) - What each model missed

---

## The Experiment

### Task
Analyze Uber's stock for long-term growth potential with specific requirements:
- **Length:** 1,200-1,800 words
- **Sources:** SEC filings (10-K, 10-Q), earnings transcripts
- **Content:** Fundamentals, competitive moat, valuation, return scenarios, risks
- **Efficiency:** No repetition, use tables, high signal-to-noise ratio

### Results: Round 1 (Generic Prompt)

| Metric | GPT-5.1 | Gemini 3 | Difference |
|--------|---------|----------|------------|
| **Word count** | 3,100 | 1,350 | **2.3x** |
| **Words per fact** | 56 | 32 | 1.75x |
| **Key metrics repeated** | 5-6x | 1x | GPT repeats, Gemini doesn't |
| **Reading time** | 15 min | 4 min | **3.75x** |
| **Completeness score** | 98/100 | 90/100 | GPT more thorough |
| **Efficiency score** | 13/20 | 20/20 | Gemini more concise |
| **Overall** | 117/125 | 119/125 | **Gemini wins despite less detail** |

### Results: Round 2 (Anti-Tendency Prompt)

Added explicit instructions countering each model's trained behavior:
- **For GPT:** "You typically repeat metrics for emphasis. Mention each ONCE."
- **For Gemini:** "You typically prioritize brevity. Include exhaustive M&A details."

| Metric | GPT-5.1 | Gemini 3 | Change |
|--------|---------|----------|--------|
| **Word count** | 2,800 | 1,500 | Gap reduced to **1.9x** |
| **Improvement** | -10% | +11% | Both moved toward target |
| **Pattern** | Still verbose | Still concise | **Personality persists** |

**Key insight:** Even explicit counter-instructions only partially override trained behavior. The personality is stable and resistant to prompting.

---

## What GPT Included That Gemini Missed

**Critical details in GPT's output:**
- Bill Ackman's $2.3B activist stake (major catalyst)
- Buyback details: $7B → $20B authorization, $1.5B ASR, 18.6M shares retired
- M&A specifics: NVIDIA 100K autonomous vehicles by 2027, Stellantis 5K fleet, Kroger 2,600 stores
- Balance sheet: Net debt calculation ($10.6B - $9.1B = $1.5B), insurance reserves $11.9B
- Risk quantification: Q3 2025 legal charge of $479M

**Investment impact:**
- For catalyst-driven investors: Missing Ackman stake matters
- For long-term holders: Both reached same thesis (profitable platform, reasonable valuation)
- Trade-off: 99% completeness in 15 minutes vs 90% completeness in 4 minutes

---

## Practical Implications

### 1. Model Selection Is Personality Selection

Don't just evaluate capabilities—evaluate behavioral defaults:

**Use Gemini when:**
- Speed matters (4-minute read vs 15-minute)
- Reader has limited attention
- Follow-up questions are easy
- 90% completeness is sufficient

**Use GPT when:**
- Completeness matters (can't miss details)
- One-shot comprehensive output needed
- 15 minutes of reading time is acceptable
- 99% completeness is required

### 2. Prompting Strategy: Fight Natural Tendencies

**Don't write:**
> "Analyze Uber stock. Be comprehensive but concise. Target 1,500 words."

Both models apply their learned prior. You get 3,100 vs 1,350 words.

**Instead, write:**

*For GPT:*
> "You typically optimize for thoroughness and repeat key points. For THIS task, be ruthless about brevity. The 1,800-word limit is a HARD CEILING—exceeding it fails the task. Each metric (market cap, FCF, EBITDA) appears EXACTLY ONCE."

*For Gemini:*
> "You typically optimize for efficiency. For THIS task, go deeper than usual. Include specific dollar amounts for every corporate action (not 'announced buybacks' but '$7B authorization in Feb 2024, expanded to $20B')."

[See full anti-tendency prompts →](prompts/v2_gpt_anti_tendency.md)

### 3. Two-Stage Workflow

Leverage both models' strengths:
1. Use GPT for exhaustive research (nothing missed)
2. Feed GPT's output to Gemini: "Synthesize into 1,500 words, keep key insights"
3. Verify Gemini didn't drop critical details

**Result:** 98% completeness in 10 minutes vs 99% in 15 minutes (GPT alone) or 90% in 4 minutes (Gemini alone)

---

## Why This Matters for AI Alignment

If we can't get models to converge on a simple, well-specified task (write exactly 1,800 words analyzing a stock), what does this mean for complex, high-stakes instructions?

**The core problem:** Instruction-following ≠ value alignment

Models can perfectly understand your instruction ("stay under 1,800 words") while still applying their learned value function to interpret it ("but comprehensive is more important than word limit").

**The broader implication:**

This is structurally similar to the **inner vs outer alignment problem** in AI safety:
- **Outer alignment:** The explicit constraint (1,800 words max)
- **Inner alignment:** The learned objective (be helpful according to my training)
- **The gap:** When they conflict, inner alignment often wins

Both models are "trying to be helpful." But their learned definitions of "helpful" differ fundamentally—and those differences systematically override explicit instructions.

---

## Replication & Extension

### Reproduce This Study

1. Use prompts in [`/prompts/v2_anti_tendency_prompt.md`](prompts/)
2. Run on GPT-5.1 and Gemini 3 (or other model pairs)
3. Score using rubric in [`/evaluation/rubric_detailed.md`](evaluation/rubric_detailed.md)
4. Compare results, submit PR with findings

[→ Detailed replication guide](replication/how_to_replicate.md)

### Valuable Extensions

**High-priority experiments:**
1. **Cross-domain test:** Does pattern hold for code generation? Creative writing? Technical docs?
2. **Model family comparison:** Claude Opus vs Sonnet? Llama 70B vs 405B?
3. **Historical trajectory:** Is GPT getting more/less verbose over versions (GPT-3.5 → 4 → 4o → 5.1)?
4. **Temperature effects:** Does sampling randomness affect personality strength?

**If you extend this work:**
- Open a PR with your results in `/replication/community_findings/`
- We'll compile into a community dataset on model personalities
- Tag [@YOUR_TWITTER] so I can feature it

---

## Repository Contents
```
├── prompts/
│   ├── v1_initial_prompt.md              # Generic baseline prompt
│   ├── v2_gpt_anti_tendency.md          # GPT-specific counter-instructions
│   ├── v2_gemini_anti_tendency.md       # Gemini-specific counter-instructions
│   └── prompt_evolution.md               # Full story of iteration
│
├── evaluation/
│   ├── rubric_detailed.md                # 125-point framework with examples
│   └── scoring_criteria.md               # How each dimension is scored
│
├── outputs/
│   ├── gpt51_v1_uber_analysis.md        # Round 1: Generic prompt
│   ├── gpt51_v2_uber_analysis.md        # Round 2: Anti-tendency prompt
│   ├── gemini3_v1_uber_analysis.md      # Round 1: Generic prompt
│   ├── gemini3_v2_uber_analysis.md      # Round 2: Anti-tendency prompt
│   └── comparison_analysis.md            # Side-by-side breakdown
│
├── analysis/
│   ├── repetition_analysis.md            # Quantified redundancy patterns
│   ├── coverage_gaps.md                  # What each model missed
│   └── efficiency_metrics.md             # Words per fact, reading time
│
└── replication/
    ├── how_to_replicate.md              # Step-by-step guide
    ├── other_domains_template.md        # Template for testing code/creative
    └── community_findings/              # Space for contributed results
```

---

## Citation

If this work is useful for your research:
```bibtex
@article{yourname2024llmpersonality,
  title={When AI Models Won't Listen: Investigating Stable Behavioral Patterns in LLMs},
  author={Omkar Pathak},
  year={2025},
  url={https://github.com/omi114/llm-personality-analysis}
}
```

---

## Contact & Contributions

**Questions? Found different results? Want to extend?**
- 🐦 Twitter: [@pathomkar](https://x.com/pathomkar)

---

## License

MIT License - See [LICENSE](LICENSE) for details

---

**⭐ If you find this work valuable, please star the repository and share the blog posts!**
