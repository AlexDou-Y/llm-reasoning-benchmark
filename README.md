# LLM Reasoning Benchmark: Nine LLMs, One Question, Nine Answers

**Testing Logical Consistency Across Major AI Models**

> I asked 9 leading LLMs the same working hours calculation question. The answers ranged from "you owe the company 48 hours" to "the company owes you 160 hours." Same question. Same data. Wildly different conclusions.

## Why This Matters

Large Language Models are increasingly relied upon for calculations, legal reasoning, and HR-related advice. But when given a straightforward working hours problem involving basic arithmetic and clear rules, **9 major models produced 9 different answers** - and they couldn't even agree on the *direction* of the result (who owes whom).

This isn't about trick questions or adversarial prompts. It's a real-world scenario with concrete numbers and well-defined rules.

## Quick Summary

| Model | Conclusion | Hours |
|-------|-----------|-------|
| GPT 5.4 (Deep Thinking) | You owe the company | 8 hours |
| Claude Opus 4.7 | Company owes you | 32 hours |
| Claude Sonnet 4.6 | You owe the company | 8 hours |
| Gemini 3.1 Pro | Company owes you | 80 hours |
| Qwen 3 Max (Thinking) | Company owes you | 48 hours |
| Qianwen 3.5 | Company owes you | 160 hours* |
| Doubao (Super Mode) | Company owes you | 40 hours |
| Doubao (Regular Mode) | You owe the company | 48 hours |
| DeepSeek (Expert Mode) | Company owes you | 40 hours |

*Qianwen 3.5 initially concluded 160 hours, then self-corrected to 96 hours in the same response.

## Key Findings

1. **No consensus on direction**: 3 models say the employee owes the company; 6 models say the company owes the employee.
2. **Massive numerical spread**: Answers range from -48 hours to +160 hours - a spread of 208 hours.
3. **Different base assumptions**: Models disagreed on fundamental parameters:
   - Annual standard working days: 248, 250, or 261 days
   - Whether to use the payroll calculation base (21.75 days/month) or actual working days
   - How to handle unused paid leave
4. **Self-contradiction**: At least one model (Qianwen 3.5) contradicted itself within the same response.

## Test Cases

| # | Case | Models Tested | Status |
|---|------|--------------|--------|
| 1 | [Working Hours Calculation](cases/working-hours-calculation/) | 9 | Complete |

## How to Contribute

We welcome new test cases! To contribute:

1. Fork this repository
2. Create a new directory under `cases/` with a descriptive name
3. Include:
   - `question.md` - The original question (with English translation if not in English)
   - `README.md` - Case description, results summary, and analysis
   - `results/` - Individual model responses
   - `screenshots/` - Evidence screenshots
4. Submit a pull request

### Guidelines for Good Test Cases

- Use real-world scenarios with concrete numbers
- Ensure there is a clear, verifiable correct answer
- Test logical reasoning, not knowledge retrieval
- Document the question in both original language and English
- Include timestamps and model version info when possible

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This benchmark is not intended to rank models or declare winners/losers. It aims to highlight the current state of logical reasoning in LLMs and encourage improvement. Model performance varies across different types of tasks, and results from a single test case should not be overgeneralized.

All model responses were collected in April 2026. Results may differ with future model updates.
