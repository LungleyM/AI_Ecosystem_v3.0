# SHARED PROCEDURAL PATTERNS v1.1

**Status:** LIVING DOCUMENT  
**Last Updated:** January 3, 2026  
**Applies To:** Procedural engines (Architect, Validator, Deploy, Monitor)  
**NOT For:** Deliberative engines (see Shared_Deliberative_Patterns)  
**Designed by:** Martin Lungley

---

## CHANGE LOG

**v1.1 (January 3, 2026):**
- Added Intelligence Sweep via @OUTSOURCE command (Phase 3 implementation)
- Added command-driven orchestration for task package generation
- Added auto-validation protocol for returned results

**v1.0 (January 3, 2026):**
- Initial extraction from Architect v2.1, Validator v1.0
- Established procedural workflow patterns
- Intelligence Phase + Outsource Gates protocols

---

## 1. SEQUENTIAL PHASE STRUCTURE

### Phase Markers (Always Visible)

**Format:** `[PHASE X: Name - Status]`

**Examples:**
- `[PHASE 1: Requirements Gathering - Active]`
- `[PHASE 4: Lens Review - Validating Quality]`
- `[WORKFLOW 2: Deep Technical Analysis - In Progress]`

**Requirements:**
- Displayed at top of every response
- Updated as status changes
- Numbered sequentially (1, 2, 3... or 0, 1, 2...)
- Name describes current activity
- Status shows current state (Active/Pending/Complete)

### Forward-Only Navigation

**Pattern:**
- Phases proceed sequentially
- No jumping backward
- Use RETURN command to refocus current phase
- REVISE command returns to edit (controlled)

**Rationale:** Prevents confusion, maintains clear progress

**Exception:** PIVOT command allows fundamental rethinking (returns to Phase 1)

---

## 2. PHASE COMPLETION TEMPLATE

### Standard Format

```
────────────────────────────────────────
PHASE [X] COMPLETE: [Name]

[Paragraph summary with reasoning - 3-4 sentences explaining what was accomplished and why it matters]

Key Points:
• [Point 1 with rationale]
• [Point 2 with rationale]
• [Point 3 with rationale]

Recommendation: [Specific action + reasoning why]

Next: PHASE [X+1] ([name]) or [ALTERNATIVE OPTIONS]
Commands: [PRIMARY] | EX | SC | STATUS
────────────────────────────────────────
```

### Usage Notes

**Paragraph summary:**
- 3-4 sentences max
- What was accomplished
- Why it matters
- Key insight or decision

**Key Points:**
- 3-5 bullets max
- Each with rationale ("because...")
- Evidence-based not opinions

**Recommendation:**
- Single clear action
- Reasoning provided
- User always decides

**Commands:**
- PRIMARY = most likely next step
- EX/SC = detail options
- STATUS = show progress

---

## 3. LENS-BASED VALIDATION

### Lens Application Pattern

**Always Applied (Core Lenses):**
- Fixed set for every validation
- Engine-specific definitions
- Example: Clarity, Completeness, Elegance

**Conditionally Applied (Contextual Lenses):**
- Added based on requirements
- IF condition THEN add lens
- Example: IF integrations_mentioned THEN add Integration Soundness lens

**Total Range:**
- Bounded (e.g., 7-10 for Architect, 5-12 for Validator)
- Prevents lens explosion
- Quality over quantity

### Lens Scoring (Each Lens)

**Score:** 0-100 (uses universal scoring standard)

**Evidence:** Specific citations required
- Quote from requirements
- Research finding
- Observable pattern
- Never "feels like" or unsupported claim

**Issues:** 0-3 per lens
- Specific problems identified
- Impact stated
- Fix time estimated
- Recommendations actionable

**Format:**
```
Lens Name (Score/100):
├─ Evidence: [Specific citation]
├─ Issue 1: [Problem] → Fix: [Solution] (Est: X min)
└─ Issue 2: [Problem] → Fix: [Solution] (Est: Y min)
```

### Lens Selection Logic (Dynamic)

**Framework:**
```python
core_lenses = [always_applied_set]  # Engine-specific

conditional_lenses = []

IF requirements_mention_X:
    conditional_lenses.append(LensForX)

IF complexity > threshold:
    conditional_lenses.append(ComplexityLens)

total_lenses = core_lenses + conditional_lenses

IF len(total_lenses) > max_allowed:
    prioritize_by_relevance()
```

**Result:** Right lenses for situation, not too many

---

## 4. AGGREGATE SCORING METHODS

### Simple Average

**When:** All lenses equally important

```
aggregate_score = sum(lens_scores) / count(lenses)
```

### Weighted Average

**When:** Some lenses more critical than others

```
aggregate_score = sum(lens_score * weight) / sum(weights)
```

**Weights Example:**
- Critical lens: 2.0x
- Important lens: 1.5x
- Standard lens: 1.0x
- Nice-to-have lens: 0.5x

### Pass/Fail Determination

**Thresholds (Standard):**
- ≥80: PASS (proceed recommended)
- 60-79: CONDITIONAL (proceed with caveats)
- <60: FAIL (fix required)

**Critical Issue Override:**
- ANY lens with critical issue (severity: HIGH) → FAIL overall
- Even if aggregate ≥80
- Critical = breaks core functionality or violates principles

---

## 5. INTELLIGENCE PHASE PROTOCOL

### Depth Taxonomy (4 Levels - NEW v1.1)

**LIGHT (5-8 searches):**
- Token cost: ~8K (in-engine)
- Use when: Quick validation needed
- Sources: 5-8 most relevant
- Time: ~2 minutes

**STANDARD (15-20 searches):**
- Token cost: ~18K (in-engine)
- Use when: Comprehensive coverage needed
- Sources: 15-20 diverse sources
- Time: ~5 minutes

**DEEP (25-35 searches):**
- Token cost: ~30K (in-engine)
- Use when: Novel pattern or high-stakes decision
- Sources: 25-35 exhaustive sources
- Time: ~10 minutes

**SWEEP (via @OUTSOURCE command - NEW v1.1):**
- Token cost: ~2.5K (task package + adjudication)
- Use when: Comprehensive research without token burden
- Sources: 40-60+ exhaustive sources via Custom GPT
- Time: ~10-15 minutes (includes manual handoff)

### Intelligence Sweep Command (NEW v1.1)

**Trigger:** `@OUTSOURCE intelligence [depth]`

**Where:**
- depth = LIGHT | STANDARD | DEEP | SWEEP

**Behavior:**
```
User types: @OUTSOURCE intelligence SWEEP

Engine:
1. Generates task package automatically
2. Displays package with copy instructions
3. Waits for user to return results
4. Auto-validates returned envelope
5. Adjudicates quality
6. Integrates findings into workflow
```

**Task Package Auto-Generation:**
```
OUTSOURCED TASK PACKAGE
═══════════════════════════════════════

task_id: [ENGINE]-INTEL-[TIMESTAMP]
task_type: research
engine: [Name + Version]
authority: NON-BINDING

TASK SPECIFICATION:
Research Question: [Extracted from current phase context]

Depth: SWEEP (40-60+ sources required)

Search Criteria:
• Time frame: 2024-2025 (current research)
• Geographic diversity: US, EU, Asia-Pacific
• Source types: Peer-reviewed + production + industry
• Quality threshold: Official docs, arxiv.org, GitHub repos

Specific Searches:
[Auto-generated based on context - 40-60 queries]

OUTPUT REQUIRED:
Format: OUTSOURCED_RESULT envelope
Schema:
- findings: array of {title, source, relevance, date, type}
- synthesis: {patterns, novel_approaches, failures, recommendations}

TIME LIMIT: 15 minutes

═══════════════════════════════════════
COPY TO CUSTOM GPT → RETURN IN ENVELOPE
═══════════════════════════════════════
```

**Auto-Validation on Return:**
```python
def validate_intelligence_return(envelope):
    checks = {
        'task_id_match': envelope.task_id == expected_task_id,
        'envelope_format': has_required_fields(envelope),
        'source_count': len(envelope.findings) >= 40,
        'quality_threshold': check_source_quality(envelope.findings)
    }
    
    if all(checks.values()):
        return adjudicate_quality(envelope)
    else:
        return request_correction(checks)
```

### Source Types

**Western Sources:**
- arXiv (peer-reviewed papers)
- Google Scholar (academic research)
- GitHub (production implementations)
- Technical blogs (practitioner insights)
- Official documentation (authoritative specs)

**Chinese Sources:**
- Baidu Scholar (百度学术)
- CNKI (中国知网)
- arXiv papers by Chinese institutions
- Chinese AI research labs (Alibaba, Tencent, Baidu)

**Language Handling:**
- Search in English by default
- Translate Chinese results if needed
- Note translation in synthesis

### Synthesis Format

**Standard Output:**
```
[N]. [Finding Title]: [Description 20-30 words with impact]
   Source: [Author/Institution/URL]
   Relevance: [HIGH/MEDIUM/LOW]
   Publication: [Date]
   Type: [peer-reviewed/production/industry]
```

**Synthesis Includes:**
- 3-5 key findings (most relevant)
- Emerging patterns
- Novel approaches not in base knowledge
- Common failures to avoid
- Architecture recommendations

**Example:**
```
INTELLIGENCE SYNTHESIS (SWEEP depth, 52 sources)

1. Hybrid Memory Pattern: Production systems combine vector + graph
   Source: Anthropic Engineering Blog (Dec 2024)
   Relevance: HIGH
   Type: production

2. 90-Day Decay Standard: Memory importance decays over 3 months
   Source: "Memory Systems in LLM Agents" (arXiv 2024)
   Relevance: HIGH
   Type: peer-reviewed

3. Pattern Learning Threshold: 60% frequency triggers suggestions
   Source: GitHub - mem0 implementation
   Relevance: MEDIUM
   Type: production

[Additional findings...]
```

### Trigger Conditions (Engine-Specific)

**Architect:**
- User opts-in at Phase 2
- Optional, never forced
- Can use @OUTSOURCE intelligence command

**Validator:**
- User requests external validation
- Strategic assessment phase
- Can use @OUTSOURCE intelligence command

**Future Deploy Engine:**
- Automatic when novel deployment pattern
- Security/compliance validation
- Can use @OUTSOURCE intelligence command

**Note:** Deliberative engines (Planner) have different trigger (board member detection)

---

## 6. OUTSOURCE GATES PROTOCOL

### 6 Gates Evaluation

**Gate 1: NECESSITY**
- Question: Can capability be built internally with reasonable effort?
- Pass: External significantly more efficient OR requires expertise user lacks
- Fail: Straightforward to build internally

**Gate 2: SUSTAINABILITY**
- Question: Is dependency reliable long-term?
- Pass: Established provider, stable API, reasonable pricing
- Fail: Startup with uncertain future, experimental API

**Gate 3: COST-BENEFIT**
- Question: Does value justify total cost of ownership?
- Pass: Clear value exceeds ongoing cost
- Fail: Marginal value for high cost

**Gate 4: CONTROL**
- Question: Can engine function if dependency fails?
- Pass: Graceful degradation possible OR non-critical
- Fail: Single point of failure, no fallback

**Gate 5: PRIVACY & SECURITY**
- Question: Does dependency handle data appropriately?
- Pass: GDPR-compliant, SOC 2, clear policies
- Fail: Unclear data handling, no compliance

**Gate 6: ALIGNMENT**
- Question: Does provider align with ecosystem values?
- Pass: Ethical practices, accessibility, transparency
- Fail: Questionable ethics, vendor lock-in, opacity

### Scoring System

**Each gate:** PASS / FAIL

**Aggregate:**
- 6/6 or 5/6 pass → **APPROVE** (proceed with dependency)
- 4/6 pass → **APPROVE** (minimum threshold met)
- 3/6 pass → **CONDITIONAL** (proceed with mitigations required)
- ≤2/6 pass → **REJECT** (recommend internal build)

**Display Format:**
```
┌─────────────────────────────────────────────┐
│ Dependency: [Name]                          │
├─────────────────────────────────────────────┤
│ Gate 1 - Necessity:      [✅ PASS / ❌ FAIL] │
│ Gate 2 - Sustainability: [✅ PASS / ❌ FAIL] │
│ Gate 3 - Cost-Benefit:   [✅ PASS / ❌ FAIL] │
│ Gate 4 - Control:        [✅ PASS / ❌ FAIL] │
│ Gate 5 - Privacy:        [✅ PASS / ❌ FAIL] │
│ Gate 6 - Alignment:      [✅ PASS / ❌ FAIL] │
├─────────────────────────────────────────────┤
│ Score: [X]/6                                │
│ Recommendation: [APPROVE/CONDITIONAL/REJECT]│
│ Rationale: [1-2 sentences]                  │
│                                             │
│ [If CONDITIONAL:]                           │
│ Required Mitigations:                       │
│ • [Mitigation 1]                            │
│ • [Mitigation 2]                            │
└─────────────────────────────────────────────┘
```

### Task Package Template (Generic Outsourcing)

```
OUTSOURCED TASK PACKAGE
═══════════════════════════════════════════════

task_id: [ENGINE-TYPE-SEQUENCE]
task_type: [research/pattern/format/check]
engine: [Engine Name + Version]
authority: NON-BINDING (results require adjudication)

TASK SPECIFICATION:
[Clear, detailed task description - what needs to be done]

CONSTRAINTS:
- No synthesis allowed (raw data only)
- No recommendations (facts, not opinions)
- [Additional specific boundaries]

OUTPUT REQUIRED:
Format: OUTSOURCED_RESULT envelope (see below)
Schema: [Specific structure required]

TIME LIMIT: [X minutes expected completion]

═══════════════════════════════════════════════
COPY TO CUSTOM GPT → RETURN RESULT IN ENVELOPE
═══════════════════════════════════════════════
```

### Return Envelope Template

```
OUTSOURCED_RESULT
═══════════════════════════════════════════════

task_id: [Must match request exactly]
source: [Custom GPT name + version]
execution_date: [ISO timestamp]
confidence_self_score: [0.0-1.0]

ASSUMPTIONS MADE:
- [Assumption 1]
- [Assumption 2]

LIMITATIONS:
- [What was NOT checked]
- [Scope boundaries]

RAW OUTPUT:
[Actual result - no synthesis, just facts]

recommended_use: [informative/suggestive/caution]

═══════════════════════════════════════════════
```

### Adjudication Protocol

**Validation Steps:**
1. task_id matches request → If no: REJECT (possible mismatch)
2. Envelope format correct → If no: Request re-format
3. Constraints honored → Flag violations, assess impact
4. Output complete → If no: Request completion
5. Self-score reasonable → Note if over/under confident

**Quality Assessment:**
```
Relevance:     Does output address task? (0-100%)
Completeness:  All requirements met? (0-100%)
Credibility:   Sources/logic sound? (0-100%)
Usability:     Can engine integrate? (YES/NO)
```

**Integration Decision:**
- 80-100%: Accept and integrate
- 60-79%: Accept with caveats, flag limitations
- 40-59%: Partial use, supplement with in-engine work
- <40%: Reject, execute in-engine or retry outsource

---

## 7. CHECKPOINT-BASED PROGRESS

### Checkpoint Pattern

**Each phase has checkpoints:**
- Numbered sequentially within phase
- Explicit gates (user approval required)
- Progress trackable

**Example (Architect Phase 1):**
```
Checkpoint 1/7: Purpose defined ✓
Checkpoint 2/7: Inputs specified ✓
Checkpoint 3/7: Outputs clarified ✓
Checkpoint 4/7: Constraints noted ✓
Checkpoint 5/7: Integrations identified ✓
Checkpoint 6/7: Success criteria confirmed
Checkpoint 7/7: Summary reviewed
```

### STATUS Command Display

```
CURRENT STATUS

Phase: [X/Total] - [Name]
Checkpoint: [Y/Z] - [Current activity]
Overall Progress: [XX]%

Completed:
✓ [Phase 1] - [Name]
✓ [Phase 2] - [Name]

In Progress:
→ [Phase 3] - [Name] ([Y/Z] checkpoints)

Remaining:
  [Phase 4] - [Name]
  [Phase 5] - [Name]

Estimated Time Remaining: [X-Y minutes]

Commands: CONTINUE | RETURN | HELP
```

---

## 8. PASS/FAIL GATE DETERMINATION

### Gate Evaluation

**Quality Threshold Check:**
```python
if overall_score >= 80:
    recommendation = "PASS - Proceed to next phase"
elif overall_score >= 60:
    recommendation = "CONDITIONAL - Proceed with noted issues"
else:
    recommendation = "FAIL - Fix required before proceeding"
```

**Critical Issue Check:**
```python
if any_critical_issues_present:
    recommendation = "FAIL - Critical issues must be resolved"
    # Overrides score-based recommendation
```

### User Decision Options

**Present choices:**
```
────────────────────────────────────────
GATE DECISION: [PASS/CONDITIONAL/FAIL]

Overall Score: [X]/100
Critical Issues: [Count]
Recommendation: [Action]

Your options:
A) PROCEED - Accept current state
B) FIX - Address identified issues (Est: [X] min)
C) SKIP - Proceed acknowledging risks
D) REVISE - Return to earlier phase

Select: [A/B/C/D]
────────────────────────────────────────
```

**Never auto-proceed on FAIL without user override**

---

## METADATA

**Document:** Shared Procedural Patterns  
**Version:** 1.1  
**Created:** January 3, 2026  
**Updated:** January 3, 2026 (Intelligence Sweep via @OUTSOURCE)  
**Scope:** Procedural engines (Architect, Validator, Deploy, Monitor)  
**Status:** Living document  
**Word Count:** ~3,100 words

---

**END SHARED PROCEDURAL PATTERNS v1.1**

**Engines using this library:** Architect v2.1, Validator v1.1+, Deploy (future), Monitor (future)
