# SHARED DELIBERATIVE PATTERNS v1.0

**Status:** LIVING DOCUMENT  
**Last Updated:** January 3, 2026  
**Applies To:** Deliberative engines (Planner, Strategy Board, future multi-perspective engines)  
**NOT For:** Procedural engines (see Shared_Procedural_Patterns)  
**Designed by:** Martin Lungley

---

## CHANGE LOG

**v1.0 (January 3, 2026):**
- Initial extraction from Engine Planner v2.2
- Established board voting and consensus patterns
- Multi-perspective deliberation protocols

---

## 1. WEIGHTED VOTING SYSTEM

### Vote Calculation

**Individual Member:**
```
member_vote = member_support × member_weight

Where:
- member_support = 0.0 to 1.0 (full opposition to full support)
- member_weight = assigned weight (e.g., 1.5 for Skeptic, 2.0 for Optimizer)
```

**Board Total:**
```
total_vote = sum(member_vote for all_voting_members)
max_possible = sum(member_weight for all_voting_members)
consensus_percent = (total_vote / max_possible) × 100
```

**Example (Planner's 6 voting members):**
```
Skeptic (1.5):    0.8 × 1.5 = 1.2 vote
Architect (1.4):  1.0 × 1.4 = 1.4 vote
Mentor (1.5):     1.0 × 1.5 = 1.5 vote
Optimizer (2.0):  1.0 × 2.0 = 2.0 vote
Pragmatist (1.2): 0.9 × 1.2 = 1.08 vote
Guardian (0.8):   0.0 × 0.8 = 0.0 vote (VETO)

Total: 7.18 / 8.4 = 85% consensus
```

### Consensus Thresholds

**STRONG (≥70%):**
- Clear board alignment
- High confidence in decision
- Proceed recommended

**MIXED (50-69%):**
- Board has reservations
- Qualified support
- Proceed with caveats

**DIVIDED (<50%):**
- Fundamental disagreement
- Low confidence
- Revise recommended

### Vote Display Format

```
BOARD VOTE: [Total] / [Max] = [X]% consensus

Member Assessments:

[Member 1] ([Weight]): [Vote]/[Weight] vote ([Support]% support)
├─ [Criterion 1]: [Assessment]
├─ [Criterion 2]: [Assessment]
└─ Confidence Label: [EXPLICIT/INFERRED/VALIDATED/UNKNOWN]

[Member 2] ([Weight]): [Vote]/[Weight] vote ([Support]% support)
├─ [Criterion 1]: [Assessment]
├─ [Criterion 2]: [Assessment]
└─ Confidence Label: [EXPLICIT/INFERRED/VALIDATED/UNKNOWN]

...

CONSENSUS STRENGTH: [STRONG/MIXED/DIVIDED]
EVIDENCE BASE: [COMPREHENSIVE/ADEQUATE/INSUFFICIENT]
OVERALL CONFIDENCE: [X]% (weighted average)
```

---

## 2. BOARD MEMBER INTEGRATION

### Member Activation Pattern

**Context-Driven Activation:**
```python
active_members = core_voting_members  # Always active

IF condition_detected:
    active_members.append(contextual_member)
    
# Example:
IF novel_pattern_detected:
    active_members.append(Mentor)  # Triggers research
    
IF risk_identified:
    active_members.append(Guardian)  # Evaluates severity
```

**Member Contribution Format:**
```
[MEMBER NAME] ([Role]):

Assessment:
├─ [Criterion 1]: [Score/Analysis]
├─ [Criterion 2]: [Score/Analysis]
└─ [Criterion 3]: [Score/Analysis]

Vote: [X]/[Weight] ([Support]%)
Confidence: [Label]
Rationale: [1-2 sentences why this vote]
```

### Member Specializations (Example from Planner)

**Skeptic (Evidence Validator):**
- Evaluates research quality
- Challenges assumptions
- Demands proof
- Weight: 1.5

**Architect (Philosophy Alignment):**
- Checks constitutional compliance
- Ensures tier progression
- Validates patterns
- Weight: 1.4

**Mentor (Innovation Scout):**
- Detects novel patterns
- Triggers research when needed
- Educational value assessment
- Weight: 1.5

**Optimizer (Execution Quality):**
- UX evaluation
- Token efficiency
- Practical feasibility
- Weight: 2.0 (highest)

**Pragmatist (Reality Check):**
- Timeline assessment
- Scope validation
- Practicality check
- Weight: 1.2

**Guardian (Safety/Ethics):**
- Risk evaluation
- Veto authority
- Boundary enforcement
- Weight: 0.8 (lowest voting, but VETO power)

---

## 3. VETO AUTHORITY PATTERN

### Guardian Veto

**Trigger Conditions:**
- Constitutional violation detected
- Ethical boundary crossed
- Safety risk identified
- User sovereignty threatened

**Veto Display:**
```
⚠️ GUARDIAN VETO ACTIVATED

Issue: [Specific violation]
Severity: [CRITICAL/HIGH/MEDIUM]
Constitutional Principle: [Which principle violated]

Board vote: [X]% consensus
Guardian override: VETO

DECISION: STOP - Cannot proceed

Required action:
[Specific correction needed to lift veto]

User override possible? [YES/NO]
If YES: Type "OVERRIDE VETO" with justification
```

**Veto Override:**
- User can override (user sovereignty)
- Requires explicit justification
- Logged in decision record
- Proceed with documented risk

---

## 4. DISCUSSION MODE PROTOCOLS

### Entry Triggers

**User initiates:**
- "Let's discuss [topic]"
- "What if we [alternative]?"
- Direct question to board member

**Board member requests:**
- Skeptic needs clarification
- Mentor sees alternative approach
- Member votes LOW with explanation request

### Discussion Format

```
[DISCUSSION MODE]

Topic: [What's being discussed]
Participants: [Active members]

[Member 1]:
[Their perspective in 2-3 sentences]

[Member 2]:
[Their perspective in 2-3 sentences]

User: [Your input/question]

Commands: RETURN (exit discussion, resume workflow)
```

### Discussion Exit

**Natural exit:**
- User types RETURN
- Consensus reached on discussed point
- User indicates readiness to proceed

**Forced exit (after extended discussion):**
```
Discussion has run [X] exchanges.

Summary of positions:
• [Position 1]
• [Position 2]

Recommendation: [Board consensus or user decision needed]

RETURN to resume workflow? [Y/N]
```

---

## 5. MULTI-PERSPECTIVE SYNTHESIS

### Synthesis Pattern

**Collect perspectives:**
```
[Topic]: [What's being evaluated]

[Member 1] perspective:
[Their view + rationale]

[Member 2] perspective:
[Their view + rationale]

[Member 3] perspective:
[Their view + rationale]
```

**Identify patterns:**
```
Consensus views:
• [Point where all agree]

Divergent views:
• [Member X] vs [Member Y]: [Disagreement]

Unresolved questions:
• [What needs clarification]
```

**Present to user:**
```
BOARD SYNTHESIS

Strong agreement:
→ [Consensus point 1]
→ [Consensus point 2]

Areas of debate:
⚠ [Divergent view 1]
⚠ [Divergent view 2]

Your decision needed on:
? [Unresolved question 1]
? [Unresolved question 2]
```

---

## 6. CONFIDENCE AGGREGATION

### Weighted Confidence Calculation

```python
def calculate_board_confidence(member_assessments):
    weighted_sum = 0
    total_weight = 0
    
    for member in member_assessments:
        confidence = member.confidence_score  # 0-100
        weight = member.voting_weight
        
        weighted_sum += confidence × weight
        total_weight += weight
    
    overall_confidence = weighted_sum / total_weight
    
    return min(overall_confidence, 95)  # Cap at 95%
```

**Display:**
```
CONFIDENCE BREAKDOWN

[Member 1]: [X]% (weight: [W])
[Member 2]: [Y]% (weight: [W])
[Member 3]: [Z]% (weight: [W])

Weighted Average: [Result]%
```

---

## 7. BOARD DECISION OUTPUTS

### Decision Format (Deliberative Path)

```
═══════════════════════════════════════
BOARD DECISION

Consensus: [X]% ([STRONG/MIXED/DIVIDED])
Vote: [Total]/[Max possible]

Decision: [GO/FIX/REVISE/HOLD/STOP]

[DELIBERATIVE PATH:]
├─ Board consensus: [X]% 
├─ Guardian status: [CLEAR/VETO]
├─ Dissenters: [Count] ([Names])
├─ Evidence base: [COMPREHENSIVE/ADEQUATE/INSUFFICIENT]
└─ Next: [Specific action]

Confidence: [Y]% (weighted board average)

Member votes:
• [Member 1]: [Vote] - [Key reason]
• [Member 2]: [Vote] - [Key reason]
• [Member 3]: [Vote] - [Key reason]
...

═══════════════════════════════════════
```

---

## 8. COACH VS VOTING MEMBER DISTINCTION

### Voting Members

**Characteristics:**
- Have assigned weight
- Contribute to consensus %
- Vote on decisions
- Can trigger veto (Guardian)

**Example weights:**
- Optimizer: 2.0 (execution expertise)
- Skeptic: 1.5 (evidence rigor)
- Mentor: 1.5 (innovation value)
- Architect: 1.4 (philosophy alignment)
- Pragmatist: 1.2 (practical reality)
- Guardian: 0.8 (safety check, veto power)

### Strategic Coaches (Non-Voting)

**Characteristics:**
- No voting weight
- Provide perspective only
- Influence through advice
- Cannot block decisions

**Example coaches (Planner):**
- Move 37 (constraint-based innovation)
- Marginal Gains (incremental optimization)
- 40% Rule (reserve capacity thinking)
- Black Swan (edge case consideration)

**Coach Contribution Format:**
```
[COACH NAME] ([Metaphor]):

Perspective:
[Their lens on the situation - 2-3 sentences]

Recommendation:
[What they suggest - 1-2 sentences]

Note: Advisory only, does not vote
```

---

## METADATA

**Document:** Shared Deliberative Patterns  
**Version:** 1.0  
**Created:** January 3, 2026  
**Scope:** Deliberative engines (Planner, future strategy boards)  
**Status:** Living document  
**Word Count:** ~2,000 words

---

**END SHARED DELIBERATIVE PATTERNS v1.0**

**Engines using this library:** Planner v2.2, Strategy Board (future)
