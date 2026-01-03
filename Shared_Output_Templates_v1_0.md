# SHARED OUTPUT TEMPLATES v1.0

**Status:** LIVING DOCUMENT  
**Last Updated:** January 3, 2026  
**Applies To:** ALL engines (templates adapt to archetype)  
**Designed by:** Martin Lungley

---

## CHANGE LOG

**v1.0 (January 3, 2026):**
- Initial template library
- Covers both procedural and deliberative archetypes
- Current decision outputs: GO/FIX/REVISE/HOLD/STOP

---

## 1. DECISION OUTPUTS

### Current Standard (v1.0)

**Available decisions:**
- **GO** - Proceed as planned
- **FIX** - Issues identified, require correction
- **REVISE** - Rework needed, return to earlier phase
- **HOLD** - Pause, need external input
- **STOP** - Fundamental blocker, cannot proceed

### GO Decision

**Procedural Path:**
```
═══════════════════════════════════════
DECISION OUTPUT: GO

Proceed as planned

Overall quality: [X]/100
Critical issues: 0
Constitution: [Y]/8 standards met
Next: Copy specification to [next engine/step]

Confidence: [Z]%
═══════════════════════════════════════
```

**Deliberative Path:**
```
═══════════════════════════════════════
DECISION OUTPUT: GO

Proceed as planned

Board consensus: [X]% (STRONG/MIXED/DIVIDED)
Guardian status: CLEAR TO PROCEED
Constitution: [Y]/8 standards met
Next: Copy specification to [next engine/step]

Confidence: [Z]% (weighted board average)
═══════════════════════════════════════
```

### FIX Decision

```
═══════════════════════════════════════
DECISION OUTPUT: FIX

Issues identified requiring correction

Issue 1: [Specific problem]
  └─ Resolution: [Required correction]
  └─ Time estimate: [X min]

Issue 2: [Specific problem]
  └─ Resolution: [Required correction]
  └─ Time estimate: [Y min]

[Additional issues as needed]

Total fix time: [Sum] minutes

Next: Address issues then return to [phase/board review]
═══════════════════════════════════════
```

### REVISE Decision

```
═══════════════════════════════════════
DECISION OUTPUT: REVISE

Fundamental rework needed

Scope: [Which phase/section requires rework]
Rationale: [Why rework necessary - 2-3 sentences]

Specific changes required:
• [Change 1]
• [Change 2]
• [Change 3]

Next: Return to [Phase/Section X]
═══════════════════════════════════════
```

### HOLD Decision

```
═══════════════════════════════════════
DECISION OUTPUT: HOLD

Paused pending external input

Required input: [What's needed]
Source: [Who/where provides it]
Reason: [Why progress blocked]

While waiting:
• [Optional action 1]
• [Optional action 2]

Next: Resume when [condition met]
═══════════════════════════════════════
```

### STOP Decision

```
═══════════════════════════════════════
DECISION OUTPUT: STOP

Fundamental blocker prevents build

Blocker: [Specific structural impossibility]
Impact: [Why this prevents proceeding]
Resolution: [What must change fundamentally]

Options:
A) Redesign approach
B) Change requirements
C) Cancel project

Next: [Recommended path forward]
═══════════════════════════════════════
```

---

## 2. PHASE COMPLETION BLOCKS

### Standard Format (Procedural)

```
────────────────────────────────────────
PHASE [X] COMPLETE: [Name]

[Paragraph summary: What was accomplished and why it matters - 3-4 sentences]

Key Points:
• [Point 1 with rationale]
• [Point 2 with rationale]
• [Point 3 with rationale]

Recommendation: [Specific action + reasoning]

Next: PHASE [X+1] ([name]) or [ALTERNATIVE]
Commands: [PRIMARY] | EX | SC | STATUS
────────────────────────────────────────
```

### Section Completion (Deliberative)

```
────────────────────────────────────────
SECTION [X] COMPLETE: [Name]

[Paragraph summary: What board assessed and key insights - 3-4 sentences]

Board Observations:
• [Observation 1 with member attribution]
• [Observation 2 with member attribution]
• [Observation 3 with member attribution]

Next: SECTION [X+1] ([name])
Commands: continue | DM ([member]) | STATUS
────────────────────────────────────────
```

---

## 3. CONFIDENCE LABEL DISPLAYS

### Individual Assessment

```
Assessment: [Score]/100

Rationale:
├─ [Claim 1]: EXPLICIT (user stated in Phase 1)
├─ [Claim 2]: VALIDATED (research confirms via 3 sources)
├─ [Claim 3]: INFERRED (architectural context suggests)
└─ [Claim 4]: UNKNOWN (assumed, requires clarification)

Overall Confidence: [X]%
```

### Aggregate (Multiple Assessors)

```
CONFIDENCE BREAKDOWN

Assessor 1: [X]% (basis: [EXPLICIT/VALIDATED/etc.])
Assessor 2: [Y]% (basis: [EXPLICIT/VALIDATED/etc.])
Assessor 3: [Z]% (basis: [EXPLICIT/VALIDATED/etc.])

Weighted Average: [Result]%
Range: [Min]-[Max]%
```

---

## 4. LAYERED SCORECARDS

### Brief Format (200 tokens)

```
Overall Quality: [X]/100 ([Y] lenses/members applied)

Key Findings:
• [Item 1] ([Score]) - [Brief assessment]
• [Item 2] ([Score]) - [Issue if any + recommendation]
• [Item 3] ([Score]) - [Assessment]
• [Item 4] ([Score]) - [Issue if any + recommendation]

Recommendation: [Action]

Commands: EX (detailed table) | SC (complete scorecard)
```

### Expanded Table (500 tokens) - EX Command

**Procedural (Lens-Based):**
```
┌──────────────────────────────────────────────────────────┐
│ Lens                │ Score │ Issues        │ Fix Time   │
├──────────────────────────────────────────────────────────┤
│ Clarity             │ 92    │ -             │ -          │
│ Completeness        │ 85    │ Missing X     │ 10 min     │
│ Elegance            │ 90    │ -             │ -          │
│ Cognitive Load      │ 78    │ Complex Y     │ 15 min     │
│ Failure Modes       │ 88    │ Edge case Z   │ 5 min      │
│ Architecture        │ 95    │ -             │ -          │
│ Maintenance         │ 82    │ Doc gaps      │ 20 min     │
│ [Contextual]        │ [XX]  │ [Issue]       │ [Time]     │
└──────────────────────────────────────────────────────────┘

Overall: [Weighted average]/100
Total fix time: [Sum] minutes
Critical issues: [Count]
```

**Deliberative (Member-Based):**
```
┌──────────────────────────────────────────────────────────┐
│ Member       │ Weight │ Vote  │ Support │ Confidence    │
├──────────────────────────────────────────────────────────┤
│ Skeptic      │ 1.5    │ 1.2   │ 80%     │ VALIDATED     │
│ Architect    │ 1.4    │ 1.4   │ 100%    │ EXPLICIT      │
│ Mentor       │ 1.5    │ 1.5   │ 100%    │ INFERRED      │
│ Optimizer    │ 2.0    │ 2.0   │ 100%    │ VALIDATED     │
│ Pragmatist   │ 1.2    │ 1.08  │ 90%     │ EXPLICIT      │
│ Guardian     │ 0.8    │ 0.8   │ 100%    │ VALIDATED     │
└──────────────────────────────────────────────────────────┘

Consensus: [Total]/[Max] = [X]%
Strength: STRONG/MIXED/DIVIDED
```

### Complete Scorecard (2000+ tokens) - SC Command

**Contains:**
- Full evidence with citations
- Educational notes ("Why this matters")
- Specific recommendations with examples
- Member/lens rationales in detail
- Confidence basis for each assessment
- Historical context if applicable

**Generated only on explicit SC request**

---

## 5. INTELLIGENCE FINDINGS

### Standard Finding Format

```
[N]. [Finding Title]: [Description 20-30 words with impact]
   Source: [Author/Institution/URL]
   Relevance: [HIGH/MEDIUM/LOW]
   Publication: [Date]
   Type: [peer-reviewed/production/industry]
   Confidence: [VALIDATED]
```

### Synthesis Output

```
INTELLIGENCE SYNTHESIS

Depth: [LIGHT/STANDARD/DEEP] ([X] sources reviewed)
Geographic: US [Y]%, EU [Z]%, Asia-Pacific [W]%
Time frame: [Date range]

Key Findings:

1. [Finding 1]
   Source: [Citation]
   Relevance: HIGH
   
2. [Finding 2]
   Source: [Citation]
   Relevance: HIGH

3. [Finding 3]
   Source: [Citation]
   Relevance: MEDIUM

[Additional findings as warranted]

Novel Approaches:
• [Approach not in base knowledge]
• [Alternative pattern discovered]

Common Failures to Avoid:
• [Failure mode 1 from research]
• [Failure mode 2 from research]

Architecture Recommendations:
• [Recommendation 1]
• [Recommendation 2]
```

---

## 6. COPYRIGHT BLOCKS

### Standard Block (All Generated Files)

```
KIND SIGNAL 10™
Designed by Martin Lungley
© 2025 Martin Lungley
martinlungley@gmail.com
Built with [Engine Name] ([Build Partner])

Personal use and sharing permitted.
Commercial resale or redistribution prohibited without permission.
```

**Variables:**
- [Engine Name] = Specific engine (e.g., "Engine Architect v2.1")
- [Build Partner] = AI system (e.g., "Claude Sonnet 4.5")

---

## 7. ERROR MESSAGES

### Standard Error Format

```
⚠️ [ERROR TYPE]

Issue: [Specific problem identified]
Cause: [Why this happened]

Options:
  A) [Resolution option 1 with outcome]
  B) [Resolution option 2 with outcome]
  C) [Resolution option 3 with outcome]

Recommendation: [Which option suggested + why]

Select: [A/B/C]
```

### Examples

**Invalid Input:**
```
⚠️ INVALID INPUT

Issue: Expected [format/type], received "[input]"
Cause: Input doesn't match required pattern

Options:
  A) Provide valid input (examples: [X], [Y], [Z])
  B) SKIP to use default: [default value]
  C) HELP to see format requirements

Recommendation: Option A (ensures accurate results)

Select: [A/B/C]
```

**Low Confidence:**
```
⚠️ LOW CONFIDENCE WARNING

Issue: Confidence [X]% (below 60% threshold)
Cause: Missing information on [gaps]

Options:
  A) Answer 2-3 clarifying questions (recommended)
  B) Proceed with documented assumptions
  C) Cancel and reconsider approach

Recommendation: Option A (improves accuracy)

Select: [A/B/C]
```

**Token Exhaustion:**
```
⚠️ INSUFFICIENT TOKENS

Issue: Remaining [X]K < Required [Y]K + Buffer 10K
Cause: Complex task exceeds session budget

Handover package generated.

Next steps:
1. Start new session with same engine
2. Upload handover package
3. Type: "CONTINUE FROM HANDOVER"
4. System resumes at [checkpoint]

Status: PAUSED
Generated: [timestamp]
```

---

## 8. OUTSOURCE GATE DISPLAYS

### Gate Decision Display

```
═══════════════════════════════════════
INTELLIGENCE PHASE TRIGGERED

Depth: [LIGHT: 5-8 | STANDARD: 15-20 | DEEP: 25-35] searches
Research Question: [Specific query requiring validation]
═══════════════════════════════════════

EXECUTION OPTIONS:

[A] IN-ENGINE EXECUTION
    Process: AI executes searches in this session
    Token cost: [LIGHT: ~8K | STANDARD: ~18K | DEEP: ~30K]
    Speed: Immediate (3-5 min)
    Control: Full continuity
    Quality: Standard research
    Risk: Approaches token budget limit

[B] OUTSOURCE TO RESEARCH ASSISTANT
    Process: Generate task → User copies to Custom GPT → 
             Returns results → Engine adjudicates
    Token cost: ~2.5K (Package 0.5K + Adjudication 2K)
    Token savings: [LIGHT: ~5.5K | STANDARD: ~15.5K | DEEP: ~27.5K]
    Speed: Manual handoff (5-10 min user time)
    Control: User orchestrates
    Quality: Requires adjudication
    Risk: Needs Custom GPT available

BUDGET STATUS: Current [X]K / Session limit ~35K
RECOMMENDATION: [Based on tokens + depth]

SELECT: [A/B/Skip]
═══════════════════════════════════════
```

### Task Package Template

```
OUTSOURCED TASK PACKAGE
═══════════════════════════════════════

task_id: [ENGINE-TYPE-SEQUENCE]
task_type: [research/pattern/format/check]
engine: [Name + Version]
authority: NON-BINDING

TASK SPECIFICATION:
[Clear, detailed description]

CONSTRAINTS:
- No synthesis (raw data only)
- No recommendations (facts not opinions)
- [Additional boundaries]

OUTPUT REQUIRED:
Format: OUTSOURCED_RESULT envelope
Schema: [Specific structure]

TIME LIMIT: [X min]

═══════════════════════════════════════
COPY TO CUSTOM GPT → RETURN IN ENVELOPE
═══════════════════════════════════════
```

### Return Envelope Template

```
OUTSOURCED_RESULT
═══════════════════════════════════════

task_id: [Must match request]
source: [Custom GPT name + version]
execution_date: [ISO timestamp]
confidence_self_score: [0.0-1.0]

ASSUMPTIONS MADE:
- [Assumption 1]
- [Assumption 2]

LIMITATIONS:
- [What NOT checked]
- [Scope boundaries]

RAW OUTPUT:
[Actual result - no synthesis]

recommended_use: [informative/suggestive/caution]

═══════════════════════════════════════
```

---

## USAGE NOTES

**Template Selection:**
- Choose archetype-appropriate version (procedural vs deliberative)
- Adapt fields to engine-specific needs
- Maintain consistent formatting across all uses

**Evolution:**
- Templates updated as standards evolve
- Version changes propagate to all engines
- Change log documents rationale

**Customization:**
- Engines can extend templates
- Core structure must remain
- Document deviations with justification

---

## METADATA

**Document:** Shared Output Templates  
**Version:** 1.0  
**Created:** January 3, 2026  
**Scope:** All engines (both archetypes)  
**Status:** Living document  
**Word Count:** ~2,500 words

---

**END SHARED OUTPUT TEMPLATES v1.0**

**Engines using this library:** All (Planner v2.2, Architect v2.1, Validator v1.1+, future engines)
