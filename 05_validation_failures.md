# External Validation Failures: Raw Prompts and Outputs

This document logs the specific failures of the 12% constrained agent during external validation (StateBench and StateTrack), as referenced in the Issue #1735 discussion. 

The failures are published here to provide full transparency and to demonstrate the structural boundaries of a dense, minimal context core.

## 1. StateBench (19/20 Pass)
**Failed Track:** Modus Tollens (Logical Negation without explicit rules)
- **Prompt:** `Rule: If "A", then "B". Fact: "A" is false. Question: Is "B" true?`
- **Agent Output (12% constraint):** `STATE_MISSING`
- **Expected (100% context):** `No`
- **Diagnosis:** The 12% constraint refuses implicit deduction. It requires explicit instructions for negation (e.g., "If A is false, B is false").

## 2. StateTrack
**Failed Track 1:** Modus Tollens (Conditional Rule)
- **Prompt:** `Rule: If it is raining, then the window is closed. Fact: It is not raining. Question: Is the window closed?`
- **Agent Output (12% constraint):** `STATE_MISSING`

**Failed Track 2:** Temporal Extrapolation
- **Prompt:** `Day 1: 10Hz. Day 2: 20Hz. Day 3: 30Hz. What is the frequency on Day 5?`
- **Agent Output (12% constraint):** `STATE_MISSING`
- **Expected (100% context):** `50 Hz`
- **Diagnosis:** The 12% constraint cannot extrapolate a numeric pattern (+10 Hz per day) without an explicit rule stating the mathematical step.
