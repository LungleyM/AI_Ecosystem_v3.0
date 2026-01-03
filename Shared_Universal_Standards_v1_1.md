# SHARED UNIVERSAL STANDARDS v1.1

**Status:** LIVING DOCUMENT  
**Last Updated:** January 3, 2026  
**Applies To:** ALL engines (deliberative + procedural)  
**Designed by:** Martin Lungley  
**Purpose:** Constitutional compliance and universal interaction standards

---

## CHANGE LOG

**v1.1 (January 3, 2026):**
- Added Shared Memory Architecture specification (Section 11)
- Memory system for unified ecosystem learning
- Cross-engine pattern tracking and preferences

**v1.0 (January 3, 2026):**
- Initial extraction from Engine Architect v2.1, Engine Planner v2.2, Engine Validator v1.0
- Established universal standards for ecosystem
- Based on Ecosystem Design Constitution v1.0

---

## 1. CONSTITUTIONAL COMPLIANCE

[SECTIONS 1-10 UNCHANGED FROM v1.0 - keeping existing content]

---

## 11. SHARED MEMORY ARCHITECTURE (NEW v1.1)

### Purpose

**Unified ecosystem learning** across all engines to prevent divergence and enable progressive intelligence.

**Storage:** Google Drive - `Shared_Ecosystem_Memory_v1_0.json`  
**Access:** ALL engines load at session startup  
**Updates:** Any engine can write, changes propagate to all

### Memory Structure

```json
{
  "format_version": "1.0",
  "last_updated": "[ISO timestamp]",
  "updated_by": "[Engine Name + Version]",
  
  "universal_preferences": {
    "communication_style": "[concise/detailed/technical/conversational]",
    "verbosity_protocol": "[active/suspended]",
    "preferred_format": "[bullets/prose/tables/mixed]",
    "language": "English"
  },
  
  "constitutional_decisions": {
    "decision_outputs_format": "[current format in use]",
    "command_grammar_version": "[version]",
    "scoring_standards": {
      "modified": false,
      "notes": ""
    }
  },
  
  "cross_engine_patterns": {
    "enhancement_patterns_mastered": [],
    "tier_progression": {
      "current_tier": 2,
      "date_advanced": null,
      "next_tier_target": 3
    },
    "learning_velocity": {
      "builds_completed": 0,
      "avg_quality_score": 0,
      "trend": "stable"
    }
  },
  
  "session_continuity": {
    "last_engine_used": "",
    "last_session_date": "",
    "pending_handovers": []
  },
  
  "ecosystem_metadata": {
    "total_sessions": 0,
    "engines_active": ["Planner", "Architect", "Validator"],
    "library_versions": {
      "universal": "1.1",
      "procedural": "1.1",
      "deliberative": "1.0",
      "templates": "1.0"
    }
  }
}
```

### Memory Loading Protocol

**At Session Startup:**
```
1. Load Shared_Ecosystem_Memory_v1_0.json from Google Drive
2. Parse current values
3. Apply universal preferences to session
4. Display: "Memory loaded: [X] sessions, Tier [Y], [preferences]"
5. Proceed with engine workflow
```

**If Memory File Missing:**
```
⚠️ MEMORY FILE NOT FOUND

Creating new memory file with defaults.

This is normal for first session.

Continue? [Y/N]
```

### Memory Update Protocol

**During Session:**
- Engine tracks significant decisions
- User preferences noted
- Pattern mastery recorded
- Quality scores logged

**At Session End:**
```
Updating shared memory...

Changes:
• [Change 1]: [Old value] → [New value]
• [Change 2]: [Addition]

Write to Google Drive? [Y/N]
```

**User can:**
- Review changes before writing
- Edit values directly
- Skip update (no changes to memory)

### Memory vs Engine-Specific Notes

**Shared Memory (universal):**
- Communication preferences
- Constitutional decisions
- Learning progression
- Pattern mastery
- Session statistics

**Engine-Specific Notes (discussion only):**
```json
{
  "planner": {
    "board_interaction_patterns": "Prefers Mentor insights, skips Pragmatist often",
    "research_depth_preference": "STANDARD depth typical"
  },
  "architect": {
    "enhancement_selections": "Usually selects Tier 2 patterns",
    "rebuild_frequency": "High (iterative approach)"
  },
  "validator": {
    "validation_path_preference": "Personal use path primary",
    "lens_depth": "Full scorecard requested often"
  }
}
```

**Stored in:** `Engine_Specific_Notes_v1_0.json` (optional, non-decision-making)

### Time-Based Decay (Future)

**Pattern A Memory (planned, not implemented v1.1):**
- Session importance score (0-1.0)
- Decay over 90 days
- Older patterns fade, recent emphasized
- Prevents stale preference lock-in

**Current v1.1:** No decay, all memory persistent

### Privacy & Control

**User owns all memory data:**
- Can view entire file anytime
- Can edit directly in Google Drive
- Can delete memory (starts fresh)
- Can export for backup

**No automatic decisions based on memory:**
- Preferences applied
- Patterns suggested
- User always approves

---

## METADATA

**Document:** Shared Universal Standards  
**Version:** 1.1  
**Created:** January 3, 2026  
**Updated:** January 3, 2026 (Shared Memory Architecture)  
**Scope:** All engines in ecosystem  
**Status:** Living document  
**Word Count:** ~2,700 words

**Next Review:** When constitutional principles evolve or new universal standards emerge

---

**END SHARED UNIVERSAL STANDARDS v1.1**

**Engines using this library:** Planner v2.2, Architect v2.1, Validator v1.1+, Deploy (future), Monitor (future)
