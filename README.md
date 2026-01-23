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

## Contact & Contributions

**Questions? Found different results? Want to extend?**
- 🐦 Twitter: [@pathomkar](https://x.com/pathomkar)

---

## License

MIT License - See [LICENSE](LICENSE) for details

---
