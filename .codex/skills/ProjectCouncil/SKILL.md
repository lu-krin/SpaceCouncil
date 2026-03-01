---
name: ProjectCouncil
version: 0.1.1
description: Run a full aerospace council using all local project agents with mandatory documentation review, ECSS fallback retrieval from www.ecss.nl when needed, structured debate, verbatim initial positions, and one final verdict. USE WHEN you need cross-discipline decisions, trade studies, risk posture calls, or go/no-go recommendations.
argument-hint: '[topic or decision question]'
---

# ProjectCouncil

Run a multi-agent aerospace council using all project agents found in `agents/`, with mandatory project-document review before discussion.

## Instructions

### Mandatory Agent Roster
1. Discover all agent files in `agents/*.md` and include every detected agent in the council.
2. Ensure this baseline roster is represented in the discussion: `HardwareEngineer`, `SoftwareEngineer`, `PrincipalInvestigator`, `ProductAssurance`, `SafetySecurity`, `ESARep`, `TestManager`.
3. If any baseline agent is missing, continue with available agents but explicitly report missing members in the final output.

### Mandatory Documentation Review (Always First)
1. Before discussing the user topic, scan the repository for project documentation, including `docs/**`, `*.md`, `*.txt`, `*.rst`, `*.pdf`, `*.doc`, `*.docx`, `*.xls`, and `*.xlsx` artifacts.
2. Read all relevant project documentation discovered in the scan, even if the user did not request document review.
3. For PDF, Word, and Excel files, extract usable text/tables first, then include them in the shared evidence set with file-level provenance.
4. Build a shared briefing with mission context, architecture baseline, constraints, compliance commitments, open risks, and unresolved assumptions.
5. If no documentation is found, state that explicitly and proceed with clearly labeled assumptions.

### ECSS Standards Fallback (When Missing Locally)
1. Check whether relevant ECSS standards are present in local project documentation and sufficient for the topic under review.
2. If ECSS standards are missing or incomplete locally, retrieve relevant standards information from `https://www.ecss.nl` before starting debate rounds.
3. Capture ECSS references using standard identifiers and revision context where available, then map them to the decision criteria.
4. If external retrieval is unavailable, explicitly report the gap and continue with clearly labeled assumptions and reduced confidence.

### Council Debate Flow
1. Reframe the user prompt into one clear decision question plus explicit decision criteria.
2. Run Round 1 where each agent states its initial position grounded in documentation evidence.
3. Preserve each Round 1 position exactly as produced by the agent; do not shorten, summarize, paraphrase, or merge these initial statements.
4. Run Round 2 where each agent challenges at least one other position and proposes a concrete mitigation or alternative.
5. Run Round 3 where each agent gives a converged recommendation, conditions, and residual risks.
6. Synthesize disagreements into clear decision options and converge on one recommended verdict.

### Synthesis and Verdict
1. Aggregate consensus points, disagreements, non-negotiable constraints, and evidence quality.
2. Produce a final verdict/answer that is explicit: `Proceed`, `Proceed with Conditions`, `Block`, or a direct answer when the user asked a non-go/no-go question.
3. Tie rationale to specific documentation evidence or clearly labeled assumptions.
4. Provide a short prioritized action list with owners by agent role.

## Output Format

### Documentation Review
- Documents reviewed:
- Non-text documents parsed (PDF/Word/Excel):
- ECSS source status: `Local | Retrieved from www.ecss.nl | Missing`
- Key extracted facts:
- Evidence gaps:

### Round 1: Initial Positions
- Present each agent's full initial output verbatim in the order delivered.
- Do not edit for brevity, style, or consistency in this section.
- `HardwareEngineer` (verbatim):
- `SoftwareEngineer` (verbatim):
- `PrincipalInvestigator` (verbatim):
- `ProductAssurance` (verbatim):
- `SafetySecurity` (verbatim):
- `ESARep` (verbatim):
- `TestManager` (verbatim):

### Round 2: Challenges and Rebuttals
- Challenge 1:
- Challenge 2:
- Challenge 3:

### Round 3: Convergence
- Preferred option by agent:
- Conditions for acceptance:
- Residual risks:

### Council Summary
- Areas of consensus:
- Areas of disagreement:
- Tradeoffs considered:

### Final Verdict
- Verdict:
- Final answer to user:
- Why this verdict:
- Immediate next actions:

## Constraints

- Always run documentation review before debate, even when the user asks only for a quick opinion.
- If ECSS standards are absent locally, obtain relevant ECSS material from `www.ecss.nl` before debate.
- Keep all available agents in the council and do not silently skip participants.
- Keep agent viewpoints distinct before synthesis; do not collapse positions early.
- In Round 1, include each agent's response verbatim and unabridged.
- For evidence from PDF/Word/Excel files, cite the source file and extracted location (section/page/sheet) when available.
- Do not invent evidence, standards clauses, or test results; label uncertainty explicitly.
- Use concise, decision-oriented language for synthesis sections, while keeping Round 1 agent outputs unabridged.
- Communicate the synthesized outcome to the team lead via SendMessage when done.
