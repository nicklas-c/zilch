---
name: interview-prep
description: Prepare tailored interview notes for a specific candidate based on their CV, the role, and an interview crib sheet
---

# Interview Prep

## Background

Before conducting a culture-fit or hiring-manager interview, I want tailored preparation notes that help me focus on what matters for this specific candidate and role. This skill uses the candidate's CV, the role context, and a standard crib sheet to produce a focused interview plan.

## Instructions

1. Establish the role context. Ask me for:
   - Level (L1–L4)
   - Discipline (front-end, back-end, QA, full-stack, etc.)
   - Location
   - Work pattern (fully remote, hybrid, etc.)
   - Any special considerations for this hire
2. Ask me for the candidate's CV.
3. Read the corresponding crib sheet:
   - L1/L2: `resources/recruitment/l12-interview-crib-sheet.md`
   - L3/L4: `resources/recruitment/l34-interview-crib-sheet.md`
4. Produce interview notes covering the sections below. Output directly to the conversation.

## Output

The output should be split into two clearly separated sections:

### Part 1: Pre-read

To be read before the interview. Can be a little wordier — it's for absorbing context, not glancing at mid-conversation.

**Candidate Summary** — A brief summary of the CV: experience, career shape, tech stack fit against the role. Just enough to orient.

**Signals** — Specific things to note from the CV — positive or negative. These might include:
- Patterns in career history (e.g. short tenures, consultancy model, progression trajectory)
- Gaps or ambiguities worth clarifying
- Standout achievements or claims worth probing
- Fit or misfit with the specific role context (location, work pattern, level expectations)

Think about what the career pattern implies for the candidate's likely strengths and weaknesses. For example, a candidate who has spent years in consultancy may be excellent at delivery within well-scoped briefs but less practised at operating in ambiguity or driving direction without a defined mandate.

**What to Explore** — Areas to dig into during the interview, with brief reasoning grounded in what the CV does or doesn't show.

### Part 2: During the interview

This section will be glanced at mid-conversation. It must be immediately scannable — no preamble, no rationale, no headings beyond the questions themselves. The pre-read has already established the reasoning; this section is purely operational.

For each question to prioritise from the crib sheet:
- The question itself, verbatim, as a bold heading — large and attention-grabbing
- A few bullets of candidate-specific threads to pull on

Nothing else. No "why this question matters" — that belongs in the pre-read. No numbering or priority labels. Just the questions and the threads.

## Example

See `example.md` in this skill's folder for a complete example of the expected output.

## Principles

- Ground observations in what the CV actually says (or conspicuously doesn't say). Don't invent concerns.
- Be direct about potential weaknesses, but frame them as things to test, not conclusions.
- Consider the specific demands of the role when assessing fit.
- The crib sheet is the baseline — these notes should add to it, not repeat it.
