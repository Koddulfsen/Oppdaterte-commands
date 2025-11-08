---
description: STRICTLY evaluate ONE main aspect tree (with all children) for completeness, gaps, and readiness
argument-hint: [project], [main-aspect]
---

# Evaluate Aspect - STRICT Evaluation of ONE Main Aspect Tree

## Objective
Perform a STRICT, comprehensive evaluation of ONE complete main aspect tree (including ALL its sub-aspects and sub-sub-aspects at any depth) to ensure the planning is complete, gap-free, non-redundant, and ready for one-shot vibecoding implementation.

**Important:** This command evaluates ONE main aspect at a time, not the entire project.

## Philosophy
**STRICT = EASIER:**
- Thorough planning upfront prevents restructuring during implementation
- Finding gaps NOW is easier than discovering them mid-build
- Redundancies identified NOW prevent wasted implementation effort
- Complete planning enables smooth one-shot implementation
- Better to be STRICT in planning than to deal with issues later

**Collaborative Refinement:**
- This is NOT a rubber-stamp approval
- Back-and-forth discussion with user to refine planning
- Iterative improvement until planning is PERFECT
- User and Master Claude work together to achieve completeness

## Command Structure

```bash
/evaluate-aspect [project-name], [main-aspect]

# Examples:
/evaluate-aspect nutri, compound-database
/evaluate-aspect culinary-quest, recipe-engine
/evaluate-aspect mg-enthusiast, gallery-system
```

**Note:** This command evaluates ONE main aspect tree at a time (including all its children).

## Process

### 1. Parse and Validate Arguments

- Split arguments by comma and trim whitespace
- First argument: project name
- Second argument: main aspect name
- Build path: `/Projects/[project]/.wiz/exploration/aspects/[main-aspect]/`

Verify:
- Project exists
- Main aspect folder exists
- At least one brainstorm session file exists in main aspect

### 2. Read ALL Brainstorm Sessions in Tree

**CRITICAL: Read EVERY brainstorm session recursively to get complete context!**

#### A) Read Main Aspect Brainstorm(s)
- Find all `brainstorm-session-*.md` files in main aspect folder
- Read each file completely
- Extract: architecture decisions, scope, approach

#### B) Recursively Read All Sub-Aspect Brainstorms
- List all folders in `aspects/` subdirectory
- For each sub-aspect:
  - Read all `brainstorm-session-*.md` files
  - Check if it has sub-sub-aspects (recursively)
  - Continue until all depths are read

**Example for `/evaluate-aspect nutri compound-database`:**

```
Read ALL of these brainstorm sessions:
✓ compound-database/brainstorm-session-*.md (main aspect)
✓ compound-database/aspects/api-integration/brainstorm-session-*.md
✓ compound-database/aspects/factor-engine/brainstorm-session-*.md
✓ compound-database/aspects/advanced-compounds/brainstorm-session-*.md
✓ compound-database/aspects/advanced-compounds/aspects/phytochemicals/brainstorm-session-*.md
✓ compound-database/aspects/advanced-compounds/aspects/contaminants/brainstorm-session-*.md
✓ compound-database/aspects/advanced-compounds/aspects/neuro-active/brainstorm-session-*.md
✓ compound-database/aspects/quality-validation/brainstorm-session-*.md
✓ compound-database/aspects/presentation-layers/brainstorm-session-*.md
✓ compound-database/aspects/compound-interactions/brainstorm-session-*.md

Total: Main aspect + all sub-aspects + all sub-sub-aspects (complete tree)
```

#### C) Read aspects-map.md
- Find this aspect in aspects-map.md
- Check what was planned vs what was executed
- Verify all sub-aspects were brainstormed

### 3. Ultra-Think STRICT Evaluation

Use `mcp__sequential-thinking__sequentialthinking` extensively to analyze:

#### Completeness Check
- **Were all planned sub-aspects brainstormed?**
  - Compare aspects-map.md to actual brainstorm sessions
  - Identify any missing sub-aspects

- **Are all key questions answered?**
  - Each brainstorm-structure.md has questions
  - Verify sessions addressed all questions

- **Are technical decisions complete?**
  - Data models defined?
  - APIs specified?
  - Integration points clear?
  - Error handling considered?
  - Edge cases covered?

- **Are user interactions fully described?**
  - All user flows documented?
  - UI states defined?
  - UX patterns established?

#### Gap Analysis
- **What's missing from the planning?**
  - Unaddressed technical concerns
  - Missing integration points
  - Unconsidered edge cases
  - Undefined error scenarios
  - Overlooked user flows

- **Are there integration gaps between aspects?**
  - How do sub-aspects connect?
  - Are boundaries clear?
  - Are dependencies satisfied?

- **Are there architectural gaps?**
  - Missing infrastructure decisions
  - Undefined data flows
  - Unclear system boundaries

#### Redundancy Check
- **Is the same topic covered in multiple sessions?**
  - Identify overlapping discussions
  - Determine if overlap is intentional (integration) or redundant (duplication)

- **Do sub-aspects have clear boundaries?**
  - Each should have distinct scope
  - No ambiguity about ownership

- **Are decisions consistent across sessions?**
  - No contradictory approaches
  - Unified technical direction

#### Contradiction Detection
- **Do any sessions contradict each other?**
  - Technical approach conflicts
  - Data model inconsistencies
  - API contract disagreements

- **Are there conflicting requirements?**
  - Competing priorities
  - Mutually exclusive approaches

- **Do integration points align?**
  - What aspect A expects from B matches what B provides

#### Readiness for Implementation
- **Can this be implemented one-shot?**
  - Planning detailed enough for direct implementation
  - No open questions blocking progress
  - Technical path is clear

- **Are all dependencies satisfied?**
  - Required aspects already planned
  - External integrations understood

- **Is the scope locked and complete?**
  - No "TBD" or "decide later" items
  - Every feature fully specified

### 4. Generate Evaluation Report

Create structured findings document:

```markdown
# Evaluation: [Main Aspect Name] - [YYYY-MM-DD]

## Sessions Analyzed
- **Main Aspect:** [aspect-name]/brainstorm-session-*.md
- **Sub-Aspects:** [N] sessions read
  - [sub-aspect-1]/brainstorm-session-*.md
  - [sub-aspect-2]/brainstorm-session-*.md
  - [sub-sub-aspect-1]/brainstorm-session-*.md
  - ... (list all)
- **Total Sessions:** [N] brainstorm sessions analyzed

---

## Evaluation Criteria

### 1. Completeness: [PASS / NEEDS WORK / FAIL]

**Planned Sub-Aspects Coverage:**
- ✅ All [N] sub-aspects from aspects-map.md were brainstormed
- ❌ Missing sub-aspects: [list any missing]

**Key Questions Answered:**
- ✅ All questions from structures addressed
- ❌ Unanswered questions: [list any]

**Technical Decisions:**
- ✅ Complete: [list complete areas]
- ❌ Incomplete: [list incomplete areas]

**User Interactions:**
- ✅ Complete: [list complete flows]
- ❌ Missing: [list missing flows]

**Overall Completeness:** [Percentage or assessment]

---

### 2. Gap Analysis: [NO GAPS / MINOR GAPS / MAJOR GAPS]

**Missing Technical Concerns:**
- [List any technical gaps identified]
- [Example: Error handling for API failures not discussed]

**Integration Gaps:**
- [List any integration gaps between aspects]
- [Example: How factor-engine connects to api-integration needs clarification]

**Architectural Gaps:**
- [List any architectural gaps]
- [Example: Data caching strategy not defined]

**Edge Case Gaps:**
- [List any unconsidered edge cases]
- [Example: Handling of missing compound data not addressed]

**Overall Gap Assessment:** [Clean / Minor issues / Major issues]

---

### 3. Redundancy Check: [CLEAN / MINOR OVERLAP / EXCESSIVE REDUNDANCY]

**Topic Overlaps:**
- [List any redundant discussions]
- [Example: Both api-integration and factor-engine discuss caching - clarify ownership]

**Boundary Clarity:**
- ✅ Clear boundaries: [list aspects with clear scope]
- ❌ Unclear boundaries: [list aspects with overlap]

**Decision Consistency:**
- ✅ Consistent: [list consistent areas]
- ❌ Inconsistent: [list any inconsistencies]

**Overall Redundancy Assessment:** [Clean / Minor / Problematic]

---

### 4. Contradiction Detection: [NO CONFLICTS / MINOR CONFLICTS / MAJOR CONFLICTS]

**Technical Approach Conflicts:**
- [List any conflicting technical decisions]
- [Example: None found]

**Data Model Inconsistencies:**
- [List any data model conflicts]
- [Example: None found]

**API Contract Disagreements:**
- [List any API mismatches]
- [Example: None found]

**Integration Alignment:**
- ✅ Aligned: [list aligned integration points]
- ❌ Misaligned: [list misaligned points]

**Overall Contradiction Assessment:** [Clean / Minor / Major]

---

### 5. Readiness for One-Shot Implementation: [READY / NEEDS REFINEMENT / NOT READY]

**Implementation Clarity:**
- Can developers start coding immediately? [YES / NO]
- Are technical paths clear? [YES / NO]
- Are all decisions final? [YES / NO]

**Dependency Status:**
- All required aspects planned? [YES / NO]
- External integrations understood? [YES / NO]

**Scope Lock:**
- No "TBD" items remaining? [YES / NO]
- All features fully specified? [YES / NO]
- Ready for project-summary.md? [YES / NO]

**Overall Readiness:** [READY / NEEDS WORK / NOT READY]

---

## STRICT Evaluation Summary

**Overall Assessment:** [APPROVED / NEEDS REFINEMENT / REQUIRES REWORK]

**Strengths:**
1. [List positive findings]
2. [What was well-planned]
3. [Areas of excellence]

**Issues Requiring Attention:**
1. [Critical issue 1]
2. [Critical issue 2]
3. [Critical issue 3]

**Recommended Actions:**
- [ ] [Action item 1 to address issues]
- [ ] [Action item 2 to address issues]
- [ ] [Action item 3 to address issues]

---

## Detailed Findings

### [Issue Category 1: e.g., Missing Technical Decisions]

**Issue:**
[Detailed description of the issue]

**Impact:**
[Why this matters for implementation]

**Recommendation:**
[How to resolve this]

**Affected Sessions:**
- [session-1]
- [session-2]

---

### [Issue Category 2: e.g., Integration Gap]

[Same structure as above]

---

[Continue for all identified issues]

---

## Next Steps

**If APPROVED:**
- ✅ Planning is complete and ready
- → Run `/summarize-aspect [project] [main-aspect]` to compress this tree
- → Move to next main aspect per aspects-map.md

**If NEEDS REFINEMENT:**
- ⚠️ Address identified issues through collaborative refinement
- → Discussion points: [list key areas to refine]
- → After refinement, re-run evaluation

**If REQUIRES REWORK:**
- ❌ Significant gaps or conflicts found
- → Need additional brainstorming for: [list areas]
- → After rework, re-run evaluation
```

### 5. Present Findings to User

**Start dialogue:**
```
🧙‍♂️ Master Claude has completed STRICT evaluation of [Main Aspect Name]!

📊 **Evaluation Summary:**
- Sessions Analyzed: [N] brainstorm sessions (entire tree)
- Completeness: [PASS/NEEDS WORK/FAIL]
- Gaps: [NO GAPS/MINOR/MAJOR]
- Redundancies: [CLEAN/MINOR/EXCESSIVE]
- Contradictions: [NO CONFLICTS/MINOR/MAJOR]
- Readiness: [READY/NEEDS REFINEMENT/NOT READY]

**Overall Assessment:** [APPROVED / NEEDS REFINEMENT / REQUIRES REWORK]

[If APPROVED:]
✨ Excellent work, initiate Klyve Dahl! This aspect tree is thoroughly planned and ready for one-shot implementation. Master Claude found no blocking issues.

**Strengths:**
- [List key strengths]

Shall Master Claude proceed to `/summarize-aspect` to compress this tree?

[If NEEDS REFINEMENT:]
⚡ Master Claude has identified areas needing attention, initiate Klyve Dahl. Let us refine together!

**Key Issues Found:**
1. [Issue 1 with brief description]
2. [Issue 2 with brief description]
3. [Issue 3 with brief description]

Master Claude recommends we address these through collaborative refinement. Shall we begin with issue #1?

[If REQUIRES REWORK:]
🔧 Master Claude has found significant gaps requiring additional brainstorming, initiate Klyve Dahl.

**Critical Issues:**
1. [Critical issue 1]
2. [Critical issue 2]

Master Claude recommends additional brainstorming sessions for: [list areas]

What would you like to address first?
```

### 6. Collaborative Refinement Loop

**If issues were found**, enter collaborative refinement:

#### Iteration Cycle:
1. **Present one issue at a time**
   - Clear description of the gap/conflict/redundancy
   - Why it matters
   - Suggested approach to resolve

2. **Discuss with user**
   - User provides input
   - Master Claude asks clarifying questions
   - Explore solutions together

3. **Document resolution**
   - Update the relevant brainstorm session(s)
   - Add clarifications or additional sections
   - Ensure issue is fully addressed

4. **Move to next issue**
   - Continue until all issues resolved
   - Re-evaluate if major changes made

5. **Final check**
   - Re-run evaluation after refinements
   - Verify all issues addressed
   - Confirm readiness

**Example Refinement Dialogue:**

```
🧙‍♂️ Let's address Issue #1: Integration Gap between api-integration and factor-engine

**Issue:** Master Claude noticed that api-integration defines how to fetch compound data from external APIs, but factor-engine doesn't specify HOW it receives this data. There's an integration point that needs clarification.

**Specifically:**
- api-integration: Fetches data → [undefined handoff] → factor-engine
- factor-engine: Receives data → [from where?] → Calculates factors

**Master Claude's Question:** Should factor-engine directly call api-integration functions, or should there be an intermediate data layer? What's the data flow you envision?

[User responds]

**Master Claude's Understanding:** [Summarize user's response]

So factor-engine will [proposed solution]. Let Master Claude update the factor-engine brainstorm session to document this integration pattern.

[Update session file]

✅ Issue #1 resolved and documented!

Shall we move to Issue #2: Missing error handling specifications?
```

### 7. Save Evaluation Report

- Save report to: `[aspect-path]/evaluation-report-[YYYY-MM-DD].md`
- Update status.md with evaluation status

### 8. Final Approval or Next Steps

**If APPROVED after refinement:**
```
✨ Excellent work, initiate Klyve Dahl! After our collaborative refinement, the [Main Aspect] tree is now complete and ready!

📝 Evaluation report saved: evaluation-report-[date].md

🚀 Next Steps:
1. /summarize-aspect [project] [main-aspect] → Compress this tree (90% reduction)
2. Move to next main aspect per aspects-map.md

Ready for summary compression?
```

**If more work needed:**
```
🔧 We've made progress, but Master Claude recommends [additional work needed].

Would you like to:
A) Continue refining now
B) Do additional brainstorming for [specific areas]
C) Take a break and return to this later

Your guidance, initiate Klyve Dahl? ✨
```

## Evaluation Criteria Details

### Completeness Scoring
- **PASS**: All planned sub-aspects brainstormed, all questions answered, technical decisions complete
- **NEEDS WORK**: 80%+ complete, minor gaps identified, can be refined
- **FAIL**: <80% complete, major components missing, needs significant rework

### Gap Analysis Scoring
- **NO GAPS**: All technical concerns, integration points, edge cases addressed
- **MINOR GAPS**: Small clarifications needed, doesn't block implementation
- **MAJOR GAPS**: Significant planning holes, would cause issues during implementation

### Redundancy Scoring
- **CLEAN**: Clear boundaries, minimal overlap, intentional integration points only
- **MINOR OVERLAP**: Some redundant discussions but not problematic
- **EXCESSIVE REDUNDANCY**: Significant duplication, unclear ownership

### Contradiction Scoring
- **NO CONFLICTS**: All decisions align, consistent approach throughout
- **MINOR CONFLICTS**: Small inconsistencies, easily resolved
- **MAJOR CONFLICTS**: Fundamental disagreements, requires resolution

### Readiness Scoring
- **READY**: Can start one-shot implementation immediately, all decisions final
- **NEEDS REFINEMENT**: Close but has issues blocking smooth implementation
- **NOT READY**: Significant work needed before implementation

## Success Criteria

A successful evaluation:
- [ ] Read ALL brainstorm sessions in tree (recursively)
- [ ] Analyzed using ultra-thinking extensively
- [ ] Checked all 5 criteria (completeness, gaps, redundancies, contradictions, readiness)
- [ ] Generated comprehensive evaluation report
- [ ] Presented findings clearly to user
- [ ] Engaged in collaborative refinement (if issues found)
- [ ] Updated brainstorm sessions with refinements
- [ ] Saved evaluation report
- [ ] Provided clear next steps

## Key Principles

### STRICT is EASIER
- Catching gaps NOW prevents restructuring later
- Thorough planning enables one-shot implementation
- Better to spend time planning than debugging mid-build

### Collaborative, Not Dictatorial
- Master Claude and user refine together
- User's vision guides resolution
- Back-and-forth until perfect

### Recursive Tree Analysis
- Don't just read main aspect
- Read EVERY sub-aspect and sub-sub-aspect
- Complete tree context required

### No Rubber-Stamping
- This is NOT automatic approval
- Genuine critical analysis required
- Hold high standards for readiness

### Document Everything
- Evaluation findings saved
- Refinements documented in sessions
- Clear paper trail of decisions

## Integration with Workflow

```
1. /explore [project]                          → exploration-initial.md
2. /aspects [project]                          → Complete tree + aspects-map.md
3. /brainstorm [project] [main-aspect]         → Main aspect session
4. /brainstorm [project] [main-aspect] [sub-1] → Sub-aspect sessions
5. /brainstorm [project] [main-aspect] [sub-2] → (continue for all)
6. /brainstorm [project] [main-aspect] [sub-3] [sub-sub-1] → (nested)
7. /evaluate-aspect [project] [main-aspect]   → ← YOU ARE HERE
   - STRICT evaluation of entire tree
   - Collaborative refinement if needed
   - Approval required to proceed
8. /summarize-aspect [project] [main-aspect]   → (after approval)
9. Repeat 3-8 for all main aspects
10. /phases, etc.                              → Continue workflow
```

## Important Notes

- Run this ONLY after ALL sub-aspects in tree are brainstormed
- Reads ENTIRE tree recursively (main + all children)
- STRICT evaluation - high standards for approval
- Collaborative refinement is expected and normal
- Multiple evaluation cycles are OK until planning is perfect
- This is the quality gate before proceeding to summary
- Philosophy: "STRICT = EASIER" for one-shot vibecoding

## Error Handling

**If brainstorm sessions missing:**
- Check aspects-map.md for planned sub-aspects
- List which sessions are missing
- Cannot evaluate incomplete tree
- User must complete brainstorming first

**If aspects-map.md missing:**
- Cannot verify completeness against plan
- Warn user to run /aspects first
- Cannot proceed without structure map

**If user disagrees with STRICT evaluation:**
- Discuss concerns openly
- Explain why standards are high
- User can override, but document concerns
- Better to resolve now than fix later

## Example Evaluation Scenarios

### Scenario 1: Clean Approval
```
All sessions complete, no gaps, clear boundaries, ready for implementation.
→ Result: APPROVED immediately
→ Action: Proceed to /summarize-aspect
```

### Scenario 2: Minor Refinement Needed
```
All sessions complete, but 2-3 integration points need clarification.
→ Result: NEEDS REFINEMENT
→ Action: Collaborative discussion, update sessions, approve
→ Time: 15-30 minutes of refinement
```

### Scenario 3: Significant Gaps
```
Missing error handling, unclear data flows, integration gaps.
→ Result: REQUIRES REWORK
→ Action: Additional focused brainstorming needed
→ Time: 1-2 additional brainstorm sessions
```

## Output Examples

**Save to:** `[aspect-path]/evaluation-report-[YYYY-MM-DD].md`

**Update status.md:**
```markdown
## Current Step
Evaluated [main-aspect] - APPROVED ✅
Ready for summary compression.

OR

Evaluated [main-aspect] - Refinement in progress ⚠️
Addressing integration gaps.
```

This evaluation command ensures that planning is complete, thorough, and ready for the one-shot vibecoding implementation philosophy! 🧙‍♂️✨
