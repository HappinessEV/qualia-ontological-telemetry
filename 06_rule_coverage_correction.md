# Correction: Rule Coverage vs. Throughput

Following external feedback (Issue #1735), we ran an additional test to determine if the 12% constrained agent's failure on Modus Tollens was due to a lack of context window (Throughput) or a lack of explicit rules (Rule Coverage).

**Hypothesis (by qingkong66):** If the agent is given an explicit negation rule, it will pass the test, proving the issue is rule coverage, not context size.

**Test:**
- **Rule 1:** If it is raining, the window is closed.
- **Rule 2 (Explicit Negation):** If there is no rain, the window is not closed.
- **Fact:** It is not raining.

**Raw Output (12% constraint):** `[EXPLICIT_NEGATION]: Нет | [Rule 2]`

**Conclusion:** 
The hypothesis is confirmed. The 12% boundary fails not due to throughput (context window limits), but due to **Rule Coverage**. The constraint requires explicit deductive rules to function. When the rule is present, the agent holds the boundary perfectly without over-forgetting.
