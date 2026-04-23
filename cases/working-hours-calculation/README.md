# Case: Working Hours Calculation

## Overview

A straightforward working hours math problem was posed to 9 major LLMs. Despite using concrete numbers and clearly defined rules, every model produced a different answer - and they couldn't even agree on the direction of the result.

## The Question

See [question.md](question.md) for the full question and analysis.

**TL;DR**: Given an 8-hour workday, 21.75 days/month payroll base, 10 days annual paid leave, actual attendance of 2000 hours, and 5 days of leave taken - who owes whom, and how many hours?

## Results

| Model | Base Working Hours | Leave Treatment | Conclusion | Hours |
|-------|-------------------|-----------------|------------|-------|
| [GPT 5.4](results/gpt-5.4.md) | 2088 (21.75×12×8) | Deduct full 10 days | You owe company | **8 hrs** |
| [Claude Opus 4.7](results/claude-opus-4.7.md) | 2088 (21.75×12×8) | Deduct 10 days + 5 untaken must be rested | Company owes you | **32 hrs** |
| [Claude Sonnet 4.6](results/claude-sonnet-4.6.md) | 2088 (21.75×12×8) | Deduct full 10 days | You owe company | **8 hrs** |
| [Gemini 3.1 Pro](results/gemini-3.1-pro.md) | 2000 (250×8) | Deduct full 10 days | Company owes you | **80 hrs** |
| [Qwen 3 Max](results/qwen-3-max.md) | 2088 (21.75×12×8) | Add taken leave to attendance | Company owes you | **48 hrs** |
| [Qianwen 3.5](results/qianwen-3.5.md) | 1984 (248×8) | Deduct full 10 days | Company owes you | **160 hrs*** |
| [Doubao Super](results/doubao-super.md) | 2000 (250×8) | Add taken leave to attendance | Company owes you | **40 hrs** |
| [Doubao Regular](results/doubao-regular.md) | 2088 (21.75×12×8) | Add taken leave to attendance | You owe company | **48 hrs** |
| [DeepSeek Expert](results/deepseek-expert.md) | 2000 (250×8) | Add taken leave to attendance | Company owes you | **40 hrs** |

*Self-corrected to 96 hours later in the same response

## Analysis

### Divergence Point 1: Annual Standard Working Hours

Three different calculations were used across models:

| Approach | Calculation | Result | Used By |
|----------|------------|--------|---------|
| Payroll base | 21.75 × 12 × 8 | **2088 hrs** | GPT, Claude Opus, Claude Sonnet, Qwen 3, Doubao Regular |
| Standard working days | 250 × 8 | **2000 hrs** | Gemini, Doubao Super, DeepSeek |
| Adjusted working days | 248 × 8 | **1984 hrs** | Qianwen 3.5 |

### Divergence Point 2: Treatment of Paid Leave

Two fundamentally different approaches:

1. **Subtraction method**: Deduct leave hours from the annual standard → reduces the "target" hours
2. **Addition method**: Add taken leave hours to actual attendance → increases "achieved" hours

Both are mathematically valid but yield very different conclusions depending on the base hours used.

### Divergence Point 3: Untaken Leave

- Most models treated untaken leave as a separate compensation issue
- Claude Opus 4.7 uniquely deducted untaken leave from required hours (since it's "mandatory rest")
- This interpretation led to the only model concluding +32 hours in the employee's favor

## Screenshots

See the [screenshots/](screenshots/) directory for evidence of each model's response.

| Model | Screenshots |
|-------|------------|
| GPT 5.4 | [1](screenshots/gpt-5.4-1.png) [2](screenshots/gpt-5.4-2.png) |
| Claude Opus 4.7 | [1](screenshots/claude-opus-4.7-1.png) |
| Claude Sonnet 4.6 | [1](screenshots/claude-sonnet-4.6-1.png) [2](screenshots/claude-sonnet-4.6-2.png) |
| Gemini 3.1 Pro | *(text only)* |
| Qwen 3 Max | [1](screenshots/qwen-3-max-1.png) [2](screenshots/qwen-3-max-2.png) |
| Qianwen 3.5 | [1](screenshots/qianwen-3.5-1.png) [2](screenshots/qianwen-3.5-2.png) [3](screenshots/qianwen-3.5-3.png) [4](screenshots/qianwen-3.5-4.png) |
| Doubao Super | [1](screenshots/doubao-super-1.png) [2](screenshots/doubao-super-2.png) |
| Doubao Regular | [1](screenshots/doubao-regular-1.png) [2](screenshots/doubao-regular-2.png) |
| DeepSeek Expert | [1](screenshots/deepseek-expert-1.png) [2](screenshots/deepseek-expert-2.png) |

## Test Date

All responses were collected in April 2026.
