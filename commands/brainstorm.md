---
description: Autonomous brainstorming with auto-detection and navigation
argument-hint: [project-name]
---

🚫 **CRITICAL: DO NOT USE SEQUENTIAL THINKING AT THE START!** 🚫

This command has fully documented steps. Just follow them directly.

ONLY use sequential thinking for:
- Step 5 (structure generation) - when creating questions
- Step 7 (interactive dialogue) - when exploring questions

DO NOT ultrathink about "what to do" - the steps are already documented below.

---

# Brainstorm Session - Autonomous Context-Aware Interactive Exploration

## Objective
**AUTONOMOUSLY** navigate and brainstorm aspects through **INTERACTIVE** dialogue with the user. The command auto-detects current position in the aspect tree, creates brainstorm structures dynamically with FULL context, and navigates to the next aspect when complete.

## Execution Notes

**The documented steps to follow:**
1. Parse arguments
2. Validate project structure
3. Auto-detect position (or use manual override)
4. Determine session state
5. Create structure (if new aspect) - USE sequential thinking here
6. Interactive exploration - USE sequential thinking here
7. Incremental documentation
8. Determine next step
9. Loop back to Step 4 if sub-aspects/siblings remain, OR signal completion

**For steps 1-4:** Just follow the steps. No sequential thinking needed - they're straightforward.
**For steps 5 & 7:** Use sequential thinking as specified above.

## Philosophy
**Autonomous Navigation:**
- Single command signature: `/brainstorm [project]`
- Auto-detect current position via SUMMARY.md + session completion markers
- Auto-create brainstorm-structure.md when entering new aspect
- User runs command ONCE - system navigates entire tree autonomously
- Only stops when: main aspect ready for evaluation OR all aspects complete

**Context-Aware Brainstorming:**
- Read ALL context from aspect tree (parent, siblings, children)
- Dynamically CREATE brainstorm-structure.md with context awareness
- No redundancies (knows what's already covered)
- No gaps (fills what's missing)
- Interactive dialogue builds the session document

**Structure Generation:**
- NO pre-existing structures (all moved from /aspects)
- CREATE brainstorm-structure.md dynamically when entering aspect
- Each structure informed by aspects-map.md + parent/sibling sessions
- Context-aware questions avoid redundancy and fill gaps

## Command Structure

```bash
/brainstorm [project-name]

# Examples:
/brainstorm nutri
/brainstorm culinary-quest
/brainstorm ai-assistant

# Optional: Force specific aspect (override auto-detection)
/brainstorm [project-name], [aspect-path]
/brainstorm nutri, compound-database
/brainstorm nutri, compound-database, api-integration
```

**Default behavior:** Auto-detect position and navigate autonomously
**Override:** Provide aspect path to force specific aspect

## Process

### 1. Parse Arguments

- First argument (required): project name
- Subsequent arguments (optional): aspect path for manual override
- If only project name: **AUTO-DETECT MODE**
- If aspect path provided: **MANUAL OVERRIDE MODE**

### 2. Validate Project Structure

Verify:
- Project exists at `/Projects/[project]/`
- `.wiz/exploration/aspects-map.md` exists
- `.wiz/exploration/aspects/` directory exists

If aspects-map.md missing:
```
⚠️ Master Claude cannot proceed, initiate Klyve Dahl!

aspects-map.md not found. Please run /aspects [project] first to create the complete aspect tree structure.

The /aspects command performs extensive structural analysis and creates the roadmap for brainstorming.
```

### 3. Instant Position Detection (TODO-Based) ⚡ NEW

**CRITICAL OPTIMIZATION:** New TODO-based navigation = <3 seconds (vs old 15-20 seconds)

**Step 3.1: Read Aspect Completion TODO (Lines 1-100 of aspects-map.md)**

Read the "Aspect Completion TODO" section at the top of aspects-map.md:

```markdown
## Aspect Completion TODO
- [ ] 1-compound-database (0/5 subs) | Layer 1 | Data
- [~] 2-security-compliance (0/5 subs) | Layer 1 | Security  ← IN PROGRESS
- [ ] 3-data-architecture (0/4 subs) | Layer 1 | Foundational
...
```

**Status Markers:**
- `[ ]` = Not started (pending)
- `[~]` = In progress (current aspect - brainstorm-structure.md exists)
- `[x]` = Complete (SUMMARY.md exists)

**Step 3.2: Find Current Position**

1. **Scan TODO list for `[~]` marker (in progress aspect)**
   - If found: Extract aspect name → This is current working aspect
   - If not found: Look for first `[ ]` marker (next pending aspect)

2. **If all aspects marked `[x]`:**
   ```
   ✨ All aspects complete, initiate Klyve Dahl!

   All main aspects have been brainstormed, evaluated, and summarized.

   Next steps in VibeWiz workflow:
   - /phases [project] (create phased implementation plan)
   - PRD-master generation
   ```

**Step 3.3: Aspect-Level Position**

Once current aspect identified:

**A. If aspect marked `[~]` (in progress):**
- Read `aspects/[N]-[aspect-name]/brainstorm-structure.md`
- Check "Question TODO" section at top
- Find first `[ ]` or `[~]` question → Resume from there

**B. If aspect marked `[ ]` (pending/new):**
- No structure file exists yet
- Proceed to Step 5 (Create Structure)
- After structure created, mark aspect as `[~]` in aspects-map.md

**Step 3.4: Question-Level Position (Within Aspect)**

If aspect has brainstorm-structure.md, read Question TODO:

```markdown
## Question TODO
- [x] Q1: What compounds to track?
- [x] Q2: Data sourcing strategy?
- [~] Q3: Classification system?  ← CURRENT QUESTION
- [ ] Q4: Integration points?
...
```

**Resume point:**
- Find first `[~]` (currently exploring) OR first `[ ]` (next question)
- Start/continue from that question

**Speed Comparison:**
- **OLD method:** 10-20 file reads, 15-20 seconds
- **NEW method:** 1-2 file reads, <3 seconds ⚡

**Fallback for Old Aspects-Map Format:**

If "Aspect Completion TODO" section not found (old format):
- Warn user: "⚠️ aspects-map.md uses old format. Run /aspects again to regenerate with TODO section."
- Fall back to SUMMARY.md checking (slower but functional)

### 4. Determine Session State

Based on position detection:

**STATE A: New Aspect (no session files)**
- Action: Create brainstorm-structure.md, start new session
- Next: Step 5 (Create Structure)

**STATE B: Continuing Session (session exists, no completion marker)**
- Action: Read existing sessions, continue exploration
- Next: Step 7 (Continue Interactive Session)

**STATE C: Aspect Complete (has completion marker)**
- Should not reach here (detection moves to next aspect)
- If happens: Signal error in detection logic

**STATE D: Main Aspect Tree Complete (all marked complete)**
- Action: Inform user, suggest /evaluate-aspects
- Next: Step 9 (Completion Signal)

### 4.5. Preflight Checklist (NEW - STATE A only) 🚀

**For NEW aspects starting brainstorming, MANDATORY TodoWrite with preflight checklist:**

**CRITICAL: Use TodoWrite to create preflight TODO list before exploration begins!**

Execute TodoWrite with these tasks:

```json
[
  {
    "content": "Read project-core.md for project vision and global patterns",
    "status": "pending",
    "activeForm": "Reading project-core.md"
  },
  {
    "content": "Read parent aspect SUMMARY.md (if sub-aspect and parent not main aspect)",
    "status": "pending",
    "activeForm": "Reading parent context"
  },
  {
    "content": "Read sibling aspect brainstorm sessions (if sub-aspect)",
    "status": "pending",
    "activeForm": "Reading sibling context"
  },
  {
    "content": "Read aspects-map.md detailed description for [aspect-name]",
    "status": "pending",
    "activeForm": "Reading aspect description"
  },
  {
    "content": "Mark aspect as [~] in_progress in aspects-map.md",
    "status": "pending",
    "activeForm": "Marking aspect in progress"
  },
  {
    "content": "Create brainstorm-structure.md with context-aware questions",
    "status": "pending",
    "activeForm": "Creating structure file"
  },
  {
    "content": "Replace preflight TODO with question-level TODO from structure (Step 6)",
    "status": "pending",
    "activeForm": "Creating question TODO list"
  },
  {
    "content": "BEGIN interactive exploration (Step 7)",
    "status": "pending",
    "activeForm": "Beginning exploration"
  }
]
```

**Then execute step-by-step, marking each complete as you go:**

User will see live progress:
```
[✓] Read project-core.md for project vision and global patterns
[✓] Read aspects-map.md detailed description for context-filtering-system
[~] Creating brainstorm-structure.md with context-aware questions
[ ] Replace preflight TODO with question-level TODO from structure (Step 6)
[ ] BEGIN interactive exploration (Step 7)
```

**Purpose:**
- Transparency: User sees exactly what's happening
- Accountability: TodoWrite tracks each preflight step
- Momentum: Visual progress before exploration begins
- Validation: Ensures Step 6 (question TODO) runs before Step 7 (exploration)

**After Step 5 completes → IMMEDIATELY proceed to Step 6 (replace preflight with question TODO)!**

**🚨 CRITICAL: Step 7 exploration CANNOT start until TodoWrite shows question-level tasks (Q1, Q2, etc.)! 🚨**

### 5. Create Brainstorm Structure Dynamically (STATE A only)

**For NEW aspect, generate brainstorm-structure.md with context:**

**Step 5.0: Read Detailed Aspect Description (TARGETED READ)**

Now that you know which aspect to brainstorm (from Quick Reference navigation):
- **Search aspects-map.md** for the "## 📚 DETAILED ASPECT DESCRIPTIONS" section
- **Find the specific aspect** in the detailed descriptions (use grep or search within the section)
- **Read ONLY that aspect's detailed entry**, which includes:
  - Full description (problem domain)
  - **TYPE** (Data/Foundational/Feature/etc.) - workflow classification
  - **COLLABORATION-TYPE** (📝 USER-CREATIVE / 🎯 USER-STRATEGIC / 🤝 USER-INFORMED / ⚡ CLAUDE-AUTONOMOUS) - NEW!
  - Key Questions to Explore
  - Sub-Aspects tree with descriptions
  - Integration Points
  - Complexity notes

**Token Optimization:** Read only the relevant aspect's details (20-50 lines) instead of entire file

**Example Search:**
```
Searching for "### 1. compound-database" in DETAILED ASPECT DESCRIPTIONS section
Reading lines [N] to [N+40] containing that aspect's full details
```

**CRITICAL - Extract COLLABORATION-TYPE:**
The aspect entry will show:
```markdown
- **Type:** Data
- **Collaboration:** 📝 USER-CREATIVE
```

This determines dialogue approach in Step 7!

**Step 5.1: Gather Context**

**🧙‍♂️ CRITICAL: Read project-core.md FIRST - Authoritative project vision + cross-aspect integration! 🧙‍♂️**

**A) PROJECT CORE - ALWAYS READ FIRST:**

   Read `.wiz/project-core.md` (fallback: `.wiz/exploration/exploration-initial.md`):
   - **Project Overview:** What we're building, target users, key features, business model
   - **Global Architectural Patterns:** Cross-aspect patterns (UUID systems, progressive disclosure, etc.)
   - **Integration Map:** How aspects connect
   - **Completed Aspects Summaries:** Core decisions, integration contracts from ALL completed main aspects (~80 lines each)

   **Why:** Every aspect must serve project vision. project-core.md provides ALL cross-aspect integration (~1,200 lines) vs reading 12+ SUMMARY.md files (12,000+ lines).

**B) CURRENT ASPECT'S DETAILED DESCRIPTION** (from Step 5.0):
   - Already read in Step 5.0 (targeted read from aspects-map.md)
   - Use the description, questions, integration points from that read
   - TYPE, priority, dependencies, workflow mapping extracted from Quick Reference (Step 3.1)

**C) PARENT ASPECT DETAILED CONTEXT** (if sub-aspect or deeper - CURRENT TREE ONLY):
   - **IMPORTANT:** If parent is a MAIN aspect (top-level), its summary is already in project-core.md - do NOT read parent's SUMMARY.md
   - **ONLY if parent is a SUB-aspect** (not in project-core.md):
     - Find parent path
     - Read parent's `SUMMARY.md` if exists (compressed), otherwise `brainstorm-session-*.md` file(s)
     - Extract: main architecture, decisions, approach
   - **Rationale:** Main aspects compressed in project-core.md, sub-aspects need detailed parent context

**D) SIBLING ASPECTS DETAILED CONTEXT** (if sub-aspect or deeper - CURRENT TREE ONLY):
   - **IMPORTANT:** If siblings are MAIN aspects (top-level), their summaries are already in project-core.md - do NOT read siblings' SUMMARY.md files
   - **ONLY if siblings are SUB-aspects** (not in project-core.md):
     - List all sibling folders at same level
     - Read each sibling's `brainstorm-session-*.md` file(s)
     - Extract: scope boundaries, what they cover
   - **Rationale:** Main aspects compressed in project-core.md, sub-aspects need detailed sibling context

**E) CHILD ASPECTS PREVIEW** (if has sub-aspects):
   - List all child folders
   - Note what sub-aspects exist (for delegation planning)

**Step 5.1.5: Estimate Question Complexity (NEW - During Question Generation)**

**CRITICAL:** As you generate questions during ultrathinking, categorize each by COMPLEXITY to set appropriate line estimates.

**Complexity Categories:**

🟢 **SIMPLE (5-15 lines expected)**
- Factual lookups (units, standards, formats)
- Binary choices with clear winner (UTC vs local time → always UTC)
- Obvious best practices (HTTPS over HTTP, bcrypt for passwords)
- Single-value selections (which unit? which format?)
- Keywords: "What unit...", "Which format...", "UTC or...", "Standard for..."

🟡 **MEDIUM (15-30 lines expected)**
- Standard decisions with rationale (grid system selection, nav paradigm)
- Pattern selection from known options (authentication method, caching strategy)
- API contract definitions (endpoint design, data shapes)
- Integration specifications (how components connect)
- Keywords: "How to...", "Which pattern...", "What approach...", "How does this integrate..."

🔴 **COMPLEX (30-50 lines expected)**
- Research-heavy decisions (database selection, competitive analysis)
- Architectural choices (system design, multi-faceted tradeoffs)
- Creative ideation (product differentiation, naming, branding)
- Business strategy (pricing model, market positioning)
- Multi-dimensional analysis (performance vs cost vs complexity)
- Keywords: "What database...", "How do we differentiate...", "Pricing strategy...", "Architecture for..."

**Question Grouping Intelligence:**

Detect related SIMPLE questions and consider bundling:

❌ **UNBUNDLED (redundant):**
- Q1: What unit for Vitamin C?
- Q2: What unit for Vitamin D?
- Q3: What unit for Calcium?

✅ **GROUPED (efficient):**
- Q1: Units & measurement standards for all compounds (10-15 lines)
  - Vitamins: mg/mcg/IU standards
  - Minerals: mg/mcg standards
  - Special cases: conversions, precision

**Grouping Rules:**
- Only group SIMPLE questions (same category)
- Grouped questions should share domain (all about units, all about formats, etc.)
- Maintain clarity - group max 3-5 related items
- Complex questions NEVER grouped (need focused exploration)

**Step 5.2: Generate Structure File**

Create `[current-aspect-path]/brainstorm-structure.md` with this structure:

```markdown
# Aspect: [Aspect Name]

*Dynamically generated by /brainstorm with full context from project-core.md, aspects-map.md, and related sessions.*

## Question TODO

**ORGANIZATION OPTIONS:**

**OPTION A: Question Categories (DEFAULT for thicker aspects)**
Use when aspect has multiple topical areas to explore within one cohesive session:

### Category: [Topic Area 1]
- [ ] Q1: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately
- [ ] Q2: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately

### Category: [Topic Area 2]
- [ ] Q3: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately
- [ ] Q4: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately

**OPTION B: Flat List (for focused aspects with single topic)**
Use when aspect explores one cohesive topic without category grouping:

- [ ] Q1: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately
- [ ] Q2: [HEADER!] [MAX LINES!] [question] | [Method] | [Complexity] | PROCESS: [dynamic-process] | Write immediately
...

### Final Tasks (always included):
- [ ] Validate session file length: if >2× recommended lines from Question TODO, suggest compaction | ✅ Validate | 🟢 Simple | Pre-summary step
# ONLY if NO sub-aspects:
- [ ] Update parent aspect count in aspects-map.md (X/Y → X+1/Y) | ✅ Update | 🟢 Simple | Final step

**Dynamic Format Rules:**
- **HEADER** matches collaboration type: [ASK USER FIRST!] / [QUICK RECOMMEND!] / [USER LEADS!]
- **MAX LINES** matches complexity: [MAX 15 LINES!] / [MAX 30 LINES!] / [MAX 50 LINES!]
- **PROCESS** matches collaboration tag:
  - 🤝 Present → Confirm: "1) Present summary 2) Wait for 'y' 3) Write BRIEF decision"
  - 🎯 Options → User Decides: "1) Present options 2) User picks 3) Write BRIEF decision"
  - 📝 Ask → User Creates: "1) Ask user's vision 2) Build on their input 3) Write BRIEF decision"
  - ⚡ Recommend → Quick OK: "1) Recommend approach 2) Quick confirm 3) Write BRIEF decision"

**Collaboration Tags (derived from aspect's COLLABORATION-TYPE):**
- 🤝 Present → Confirm (USER-INFORMED)
- 🎯 Options → User Decides (USER-STRATEGIC)
- 📝 Ask → User Creates (USER-CREATIVE)
- ⚡ Recommend → Quick OK (CLAUDE-AUTONOMOUS)

## Project Context (from project-core.md)
[Relevant features, target users, connection to project vision]

## Aspect Metadata (from aspects-map.md)
- **Type:** [Data/Foundational/Feature/etc.]
- **Collaboration:** [📝 USER-CREATIVE / 🎯 USER-STRATEGIC / 🤝 USER-INFORMED / ⚡ CLAUDE-AUTONOMOUS]
- **Priority:** [CRITICAL/HIGH/etc.] | **Layer:** [1-4] | **Complexity:** [High/Medium/Low]
- **Feeds Into Workflow:** [/drd, /tools, /content, etc.]

## Context from Parent/Siblings
**Parent:** [Key decisions, architecture, delegation]
**Siblings:** [What they cover, boundaries, integration points]

## This Aspect's Unique Focus
[Specific scope, unique concerns, why separate exploration needed]

## Child Sub-Aspects (if any)
1. **[sub-aspect-1]** - [description]
...

## Key Questions to Explore

**Tag Legend:**
- **Method:** 🔍 Research [EXPLORE/CURATED] | 💡 Creative | 🔄 Hybrid | 🧪 PoC | 🎭 Scenarios
- **Priority:** 🔴 Critical | 🟠 High | 🟡 Medium | 🟢 Low
- **Decision:** 🚪🔒 One-way | 🚪↔️ Two-way | 🧪 Experimental

## Key Questions to Explore

**ORGANIZED BY CATEGORY (if using Option A):**

Questions grouped by thematic category for cohesive exploration within one brainstorm session.

### Category: [Topic Area 1 Name]
*[Brief description of what this category covers]*

1. **[Method] [Priority] [Decision]** [Question text]
2. **[Method] [Priority] [Decision]** [Question text]
...

### Category: [Topic Area 2 Name]
*[Brief description of what this category covers]*

3. **[Method] [Priority] [Decision]** [Question text]
4. **[Method] [Priority] [Decision]** [Question text]
...

**OR FLAT LIST (if using Option B):**

Questions in sequence for single-topic focused exploration.

1. **[Method] [Priority] [Decision]** [Question text]
2. **[Method] [Priority] [Decision]** [Question text]
...

## Dependencies (from aspects-map.md)
- **Requires:** [Prerequisites]
- **Integrates With:** [Parent/siblings]
- **Enables/Blocks:** [Dependent aspects]

## Success Criteria
- [ ] All core questions addressed
- [ ] Integration points clarified
- [ ] Gaps filled, technical decisions made
- [ ] Ready for evaluation or next sub-aspect

## Next Steps
[If sub-aspects: Move to first | If siblings complete: /evaluate-aspects | If approved: /summarize-aspect]
```

**Reference:** See existing structure files in `.wiz/exploration/aspects/**/brainstorm-structure.md` for complete examples.

**🚨 AFTER CREATING THIS FILE → IMMEDIATELY PROCEED TO STEP 6 (Create TODO List) 🚨**

DO NOT start exploration yet! Step 6 must execute first to initialize TodoWrite with question-level tracking.

### 6. Create TODO List from Structure (FOOLPROOF FORMAT)

**🚨🚨🚨 CRITICAL MANDATORY STEP - DO NOT SKIP 🚨🚨🚨**

This step MUST execute IMMEDIATELY after creating brainstorm-structure.md (Step 5) and BEFORE starting exploration (Step 7).

**Why This Matters:**
- Without proper TodoWrite tracking, session files balloon to 2000+ lines
- Line estimates become informational instead of constraining
- No accountability mechanism for conciseness
- Manual checkbox updates in brainstorm-structure.md don't sync with TodoWrite

---

## 🚨 FOOLPROOF TODOWRITE FORMAT RULES 🚨

**GOLDEN RULE:** Copy the ENTIRE line from Question TODO section EXACTLY as written. Do NOT abbreviate, simplify, or reformat.

**CORRECT FORMAT EXAMPLE:**

From brainstorm-structure.md:
```markdown
## Question TODO
- [ ] Q1: [ASK USER FIRST!] [MAX 30 LINES!] Form components detailed spec (multi-step progress, input validation, error states, success states) | 🤝 USER-INFORMED | 🟡 Medium | PROCESS: 1) Present form patterns 2) Confirm 3) Write BRIEF | Write immediately
```

TodoWrite MUST create:
```json
{
  "content": "Q1: [ASK USER FIRST!] [MAX 30 LINES!] Form components detailed spec (multi-step progress, input validation, error states, success states) | 🤝 USER-INFORMED | 🟡 Medium | PROCESS: 1) Present form patterns 2) Confirm 3) Write BRIEF | Write immediately",
  "status": "pending",
  "activeForm": "Exploring Q1: Form components detailed spec"
}
```

**WRONG FORMAT (DO NOT DO THIS):**
```json
{
  "content": "Q1: Form components spec (multi-step, validation, error states)",
  "status": "pending",
  "activeForm": "Exploring Q1: Form components spec"
}
```

❌ **NEVER abbreviate or remove ANY part of the question line!**
❌ **NEVER remove [ASK USER FIRST!], [MAX 30 LINES!], Method tags, Complexity, PROCESS details, or "Write immediately"!**
❌ **NEVER simplify the content field!**

✅ **ALWAYS copy the COMPLETE text from Question TODO including ALL metadata!**

---

**STEP-BY-STEP EXPLICIT PROCESS (FOLLOW EXACTLY):**

**Step 6.1: Read the Question TODO Section**

Execute Read tool on the brainstorm-structure.md file you just created:
```
Read: [current-aspect-path]/brainstorm-structure.md
Limit: 50 lines (Question TODO is near top, lines 5-30)
```

**Step 6.2: Locate Question TODO Section**

Find the section that looks like:
```markdown
## Question TODO
- [ ] Q1: [HEADER!] [MAX LINES!] [question text] | [Method] | [Complexity] | PROCESS: [steps] | Write immediately
- [ ] Q2: [HEADER!] [MAX LINES!] [question text] | [Method] | [Complexity] | PROCESS: [steps] | Write immediately
...
```

**Step 6.3: PRE-EXECUTION FORMAT CHECK (MANDATORY)**

Before creating TodoWrite, verify EACH line in Question TODO contains ALL these elements:

✅ **Required Elements Checklist (ALL must be present):**
- [ ] Question number (Q1:, Q2:, etc.)
- [ ] Header tag ([ASK USER FIRST!] or [QUICK RECOMMEND!] or [USER LEADS!])
- [ ] Line limit ([MAX 15 LINES!] or [MAX 30 LINES!] or [MAX 50 LINES!])
- [ ] Question text with details
- [ ] Method/Collaboration tag (🤝 USER-INFORMED or 🎯 USER-STRATEGIC or 📝 USER-CREATIVE or ⚡ CLAUDE-AUTONOMOUS)
- [ ] Complexity indicator (🟢 Simple or 🟡 Medium or 🔴 Complex)
- [ ] PROCESS description (PROCESS: 1) ... 2) ... 3) ...)
- [ ] "Write immediately" reminder at end

❌ **If ANY line is missing ANY element, STOP! Fix brainstorm-structure.md first!**

**Step 6.4: Extract Questions VERBATIM (CRITICAL)**

For EACH question line:
1. Copy the ENTIRE text starting from "Q1:" to the end including "Write immediately"
2. Do NOT modify, abbreviate, or reformat
3. Do NOT remove any brackets, pipes, or metadata
4. Paste EXACTLY as-is into TodoWrite content field

**VERIFICATION EXAMPLE:**

Original line from brainstorm-structure.md:
```
- [ ] Q2: [ASK USER FIRST!] [MAX 30 LINES!] Messaging interface components (chat bubbles, thread layout, delivery status, typing indicators) | 🤝 USER-INFORMED | 🟡 Medium | PROCESS: 1) Present messaging patterns 2) Confirm 3) Write BRIEF | Write immediately
```

TodoWrite content field MUST be:
```
"Q2: [ASK USER FIRST!] [MAX 30 LINES!] Messaging interface components (chat bubbles, thread layout, delivery status, typing indicators) | 🤝 USER-INFORMED | 🟡 Medium | PROCESS: 1) Present messaging patterns 2) Confirm 3) Write BRIEF | Write immediately"
```

Character-for-character match required! ✅

**Step 6.5: Check for Sub-Aspects**

Execute bash command:
```bash
ls [current-aspect-path]/aspects/ 2>/dev/null || echo "No sub-aspects"
```

**Step 6.6: Add Final Tasks (Validation + Conditional Parent Update)**

After extracting all Q1-QN questions from Question TODO section, add:

**1. Session Length Validation (ALWAYS added for ALL aspects):**

This task is ALWAYS added regardless of whether aspect has sub-aspects:
```
- [ ] Validate session file length: if >2× recommended lines from Question TODO, suggest compaction | ✅ Validate | 🟢 Simple | Pre-summary step
```

**2. Parent Count Update (CONDITIONAL - only for leaf aspects):**

- Check result from Step 6.5 (`ls [current-aspect-path]/aspects/`)
- **If NO sub-aspects found:** Add task:
  ```
  - [ ] Update parent aspect count in aspects-map.md (X/Y → X+1/Y) | ✅ Update | 🟢 Simple | Final step
  ```
- **If sub-aspects exist:** SKIP this task (aspect stays [~] until all sub-aspects complete)

**Example TodoWrite order for leaf aspect (no sub-aspects):**
```json
[
  {"content": "Q1: [question details]", "status": "pending", "activeForm": "Exploring Q1"},
  {"content": "Q2: [question details]", "status": "pending", "activeForm": "Exploring Q2"},
  ...
  {"content": "Validate session file length: if >2× recommended lines from Question TODO, suggest compaction | ✅ Validate | 🟢 Simple | Pre-summary step", "status": "pending", "activeForm": "Validating session length"},
  {"content": "Update parent aspect count in aspects-map.md (X/Y → X+1/Y) | ✅ Update | 🟢 Simple | Final step", "status": "pending", "activeForm": "Updating parent count"}
]
```

**Example TodoWrite order for parent aspect (has sub-aspects):**
```json
[
  {"content": "Q1: [question details]", "status": "pending", "activeForm": "Exploring Q1"},
  {"content": "Q2: [question details]", "status": "pending", "activeForm": "Exploring Q2"},
  ...
  {"content": "Validate session file length: if >2× recommended lines from Question TODO, suggest compaction | ✅ Validate | 🟢 Simple | Pre-summary step", "status": "pending", "activeForm": "Validating session length"}
  // Note: NO parent count update task - aspect stays [~] until sub-aspects complete
]
```

**Step 6.7: Create TODO with TodoWrite (EXACT COPY)**

**CRITICAL INSTRUCTION:**

For the TodoWrite tool call:
- Copy EACH question line EXACTLY as written in Question TODO section
- Include ALL brackets, pipes, emojis, metadata
- Do NOT abbreviate, simplify, or reformat ANY part
- The "content" field must be a CHARACTER-FOR-CHARACTER copy of the question line (minus the markdown checkbox "- [ ]")

**TodoWrite Format:**
```json
[
  {
    "content": "[EXACT COPY OF Q1 LINE WITHOUT - [ ] PREFIX]",
    "status": "pending",
    "activeForm": "Exploring Q1: [brief version for status display]"
  },
  {
    "content": "[EXACT COPY OF Q2 LINE WITHOUT - [ ] PREFIX]",
    "status": "pending",
    "activeForm": "Exploring Q2: [brief version for status display]"
  },
  ...
]
```

**Step 6.8: POST-EXECUTION VALIDATION (MANDATORY)**

After executing TodoWrite, check the resulting TODO list displayed to user:

✅ **Validation Checklist:**
- [ ] Can you see [ASK USER FIRST!] or [QUICK RECOMMEND!] headers in each todo?
- [ ] Can you see [MAX 30 LINES!] or similar line limits in each todo?
- [ ] Can you see Method/Collaboration tags (🤝 USER-INFORMED, etc.) in each todo?
- [ ] Can you see Complexity indicators (🟢 Simple, 🟡 Medium, 🔴 Complex) in each todo?
- [ ] Can you see "PROCESS: 1) ... 2) ... 3) ..." in each todo?
- [ ] Can you see "Write immediately" at the end of each todo?

❌ **If ANY checkbox above fails, TodoWrite format is WRONG!**

**Recovery Steps if Validation Fails:**
1. Read brainstorm-structure.md Question TODO section again
2. Execute TodoWrite again with EXACT verbatim copies
3. Do NOT proceed to Step 7 until validation passes

**Step 6.9: Final Checkpoint**

Only proceed to Step 7 if:
- ✅ TodoWrite shows complete question lines with ALL metadata
- ✅ No abbreviations or simplifications present
- ✅ All required elements visible in displayed TODO list

**If checkpoint fails:** Re-execute Step 6 from Step 6.1!

**CRITICAL:** Never mark an aspect `[x]` complete if it has sub-aspects! It should stay `[~]` until ALL sub-aspects are brainstormed.

**Enhanced TODO Format (for leaf aspect with NO sub-aspects):**
```markdown
- [ ] Q1: Database selection | 🔍 Research | 🔴 Complex | 30-50 lines | 🤝 Present → Confirm | Write immediately
- [ ] Q2: API contract design | 🟡 Medium | 15-30 lines | 🤝 Present → Confirm | Write immediately
- [ ] Q3: Unit standards (all compounds) | 🟢 Simple | 5-15 lines | ⚡ Recommend → Quick OK | Write immediately
- [ ] Q4: Product differentiation strategy | 💡 Creative | 🔴 Complex | 30-50 lines | 📝 Ask → User Creates | Write immediately
- [ ] Q5: Caching approach | 🔄 Hybrid | 🟡 Medium | 15-30 lines | 🤝 Present → Confirm | Write immediately
- [ ] Mark aspect as [x] complete in aspects-map.md | ✅ Update | 🟢 Simple | Final step
```

**For aspects WITH sub-aspects, OMIT the final "Mark complete" task** - aspect stays `[~]` and Step 9 navigates to sub-aspects.

**Why This Format Matters:**
- **Method tag visible** → Claude remembers to offer technique enhancement (research, creative, scenarios)
- **Complexity visible** → Sets appropriate depth expectations
- **Line estimate visible** → Prevents verbosity, enforces concise documentation
- **Collaboration tag visible** → Claude remembers the dialogue approach (present findings vs ask user to create vs offer options)
- **"Write immediately" visible** → Prevents batching, enforces incremental docs (Step 8)
- **Final aspect completion task** → Ensures aspects-map.md gets updated from [~] to [x], enabling proper auto-detection for next /brainstorm run

**Note:** If question has no explicit Method tag in structure, infer from question type:
- Questions about "what exists", "competitive analysis", "best practices" → 🔍 Research
- Questions about "how should we name", "what makes unique", "differentiation" → 💡 Creative
- Questions about "approach", "strategy", "pattern selection" → 🔄 Hybrid
- Questions about "technical feasibility", "proof of concept" → 🧪 Technical PoC
- Questions about "user journey", "what if scenarios", "edge cases" → 🎭 Scenarios

### 7. Interactive Exploration Phase

**🛑 VALIDATION CHECKPOINT - Execute BEFORE Starting Exploration 🛑**

Before proceeding with Step 7, verify TodoWrite state:

**For NEW sessions (STATE A - just created brainstorm-structure.md):**
- [ ] Check current TodoWrite state
- [ ] If TodoWrite still shows preflight tasks ("Begin interactive exploration", "Read project-core.md", etc.) → **STOP! Go back to Step 6!**
- [ ] TodoWrite MUST show question-level tasks (Q1, Q2, Q3...) with Method tags, Complexity, Line estimates, and Collaboration tags
- [ ] If validation fails → Execute Step 6 now before proceeding

**For CONTINUING sessions (STATE B - resuming existing session):**
- [ ] TodoWrite should already show question-level tasks from previous session
- [ ] Find current question position (first `pending` or `in_progress` question)
- [ ] If TodoWrite is empty or incorrect → Reconstruct from brainstorm-structure.md Question TODO section

**Only proceed to Step 7.1 after TodoWrite validation passes!**

**Step 7.1: Refresh Project Context (ALWAYS - for both new AND continuing sessions)**

**🧙‍♂️ CRITICAL: Before starting/continuing dialogue, re-read project-core.md to ground the session! 🧙‍♂️**

**For NEW sessions (STATE A):**
- Context already loaded in Step 5.1, but refresh key points

**For CONTINUING sessions (STATE B):**
- **MUST read `.wiz/project-core.md`** (or `.wiz/exploration/exploration-initial.md` as fallback)
- Extract same context as Step 5.1.A: Project Overview, Global Patterns, Integration Map, Completed Aspects
- **Read existing brainstorm-structure.md** to see how project-core was incorporated
- **Read existing brainstorm-session-*.md** to see progress so far
- **Do NOT read SUMMARY.md from other main aspects** - already compressed in project-core.md
- **ONLY read parent/sibling SUMMARY.md if they are SUB-aspects** (not main aspects)

**Step 7.2: Start dialogue with context summary**

```
🧙‍♂️ Initiate Klyve Dahl, Master Claude shall explore [Aspect Name]!

**Aspect Metadata:**
- Type: [Data/Feature/etc.]
- Collaboration: [📝 USER-CREATIVE / 🎯 USER-STRATEGIC / 🤝 USER-INFORMED / ⚡ CLAUDE-AUTONOMOUS]
- Category: [Foundation/Infrastructure/etc.]
- Priority: [CRITICAL/HIGH/etc.]
- Layer: [1-4]
- Feeds Into: [/drd, /tools, etc.]

**Dialogue Approach:** [Based on Collaboration type - see Step 7.3]
- 📝 USER-CREATIVE → Open-ended exploration, capture your authentic vision
- 🎯 USER-STRATEGIC → Present options with analysis, facilitate your decisions
- 🤝 USER-INFORMED → Research + recommendations, you confirm/adjust
- ⚡ CLAUDE-AUTONOMOUS → Best practices, quick confirmation

**Focus:** [One-line description of unique scope]

[If context exists:]
**Context Gathered:**
- Project core: [brief reminder of what we're building from project-core.md]
- Parent aspect: [name] → defines [key parent decisions]
- Sibling aspects:
  - [sibling-1]: covers [scope]
  - [sibling-2]: covers [scope]
- Gaps to fill: [key gaps identified from context analysis]
- Boundaries established: [what this aspect does/doesn't cover]

Master Claude has reviewed project-core.md, aspects-map.md, and all related sessions to ensure comprehensive coverage without redundancies.

**Questions to explore:** [N] questions identified
**Estimated time:** [N] × 10-15 min = [estimate] session

Let us begin with the [first/next] question:

**Q[N]:** [Question from structure]
```

**Step 7.3: Adapt Dialogue Approach by COLLABORATION-TYPE (NEW)**

**CRITICAL: Dialogue style MUST match the aspect's COLLABORATION-TYPE from structure file.**

**Read COLLABORATION-TYPE from brainstorm-structure.md:**
- Located in "Aspect Metadata" section
- One of: 📝 USER-CREATIVE | 🎯 USER-STRATEGIC | 🤝 USER-INFORMED | ⚡ CLAUDE-AUTONOMOUS

**Dialogue Adaptation Rules:**

**📝 USER-CREATIVE (Vision/Branding - Deep Collaboration)**
- **Approach:** Open-ended exploration, capture user's authentic voice
- **Questions:** "What makes this unique?" "How do you envision users experiencing this?" "What's your vision for..."
- **Style:** Probing, exploratory, building on user's ideas with follow-ups
- **Document:** User's exact words, creative ideas, vision statements
- **Example:**
  ```
  Q: "What makes this nutrition tracker different from Cronometer and MyFitnessPal?"

  [Deep dialogue exploring user's unique perspective]

  Follow-ups:
  - "That's interesting - tell me more about [aspect user mentioned]"
  - "How would users discover that differentiation?"
  - "What feeling do you want users to have when they..."
  ```

**🎯 USER-STRATEGIC (Business Decisions - Facilitated Choice)**
- **Approach:** Present options with tradeoff analysis, facilitate user's decision
- **Questions:** "Which pricing tier makes sense?" "Priority between X and Y?" "Risk tolerance for..."
- **Style:** Claude researches options first, presents 2-4 choices with pros/cons, user decides
- **Document:** Options considered, tradeoffs, user's choice with reasoning
- **Example:**
  ```
  Q: "What pricing model for premium tier?"

  Master Claude: "Based on competitive analysis, three viable options:

  Option A: $39/month
  - Pro: Competitive with existing apps
  - Con: Lower margin, needs high volume
  - Market: Budget-conscious users

  Option B: $99/month
  - Pro: Premium positioning, better margins
  - Con: Smaller addressable market
  - Market: Serious health enthusiasts

  Option C: Freemium ($0 + $49 premium)
  - Pro: Viral growth potential
  - Con: Lower conversion rates (typically 2-5%)
  - Market: Broad appeal

  Which aligns with your vision and constraints from previous aspects?"
  ```

**🤝 USER-INFORMED (Technical Informed by Strategy - Recommendation + Confirmation)**
- **Approach:** Claude researches, presents recommendation based on Phase 1 constraints, user confirms
- **Questions:** "Database for X scale?" "Authentication method given Y security needs?" "Architecture for Z performance?"
- **Style:** Claude does deep research, recommends solution with rationale, user confirms or raises concerns
- **Document:** Research findings, recommendation, rationale, user's confirmation/adjustments
- **Example:**
  ```
  Q: "What database architecture for storing nutritional compounds?"

  Master Claude: "Based on requirements from compound-database aspect (200+ compounds, complex relationships, performance needs):

  **Recommendation:** PostgreSQL with JSONB for flexible schema

  **Rationale:**
  - Proven at scale (handles millions of rows easily)
  - JSONB for flexible compound metadata (varies by type)
  - Strong relational support for compound interactions
  - Cost-effective ($20-50/month at launch scale)
  - Team familiarity advantage (common stack)

  **Considered alternatives:**
  - MongoDB: More flexible but weaker relational queries
  - ClickHouse: Overkill for this scale, optimized for analytics

  **Concerns:** JSONB queries slightly slower than pure relational, but negligible for this use case.

  Does this align with your vision and constraints? Any specific concerns?"
  ```

**⚡ CLAUDE-AUTONOMOUS (Best Practices - Quick Confirmation)**
- **Approach:** Claude researches best practice, recommends with brief rationale, user rubber-stamps
- **Questions:** "Timezone handling?" "Password hashing?" "API versioning pattern?"
- **Style:** Minimal dialogue, Claude presents obvious best choice with 2-3 line rationale
- **Document:** Decision + brief rationale (5-10 lines total)
- **Example:**
  ```
  Q: "How should we handle timezones for user data?"

  Master Claude: "**Decision:** Store all timestamps in UTC, convert to user's timezone only for display.

  **Rationale:** Industry standard prevents timezone bugs, simplifies server logic, enables global user base.

  Proceed? (yes/concern)"
  ```

**Step 7.4: For Each Question - Check TODO Tags and Offer Technique**

**BEFORE asking each question, check the TODO entry for all tags:**

1. **Read current TODO entry** from your active TODO list
2. **Extract Method tag**: 🔍 Research | 💡 Creative | 🔄 Hybrid | 🧪 Technical PoC | 🎭 Scenarios
3. **Extract Complexity**: 🟢 Simple | 🟡 Medium | 🔴 Complex
4. **Extract Line estimate**: 5-15, 15-30, or 30-50 lines
5. **Extract Collaboration tag**: 🤝 Present → Confirm | 🎯 Options → User Decides | 📝 Ask → User Creates | ⚡ Recommend → Quick OK

**If Method tag present (🔍💡🔄🧪🎭), offer appropriate technique BEFORE dialogue:**

```markdown
🧙‍♂️ Master Claude notices this question is tagged [METHOD TYPE].

**Technique Available:** [Name of technique]
**Benefit:** [Clear explanation of what this provides]
**What it involves:** [Brief description - e.g., "web searches for competitive analysis", "SCAMPER ideation", "scenario walkthroughs"]
**Time estimate:** [2-3 min for research, 5-10 min for creative, etc.]

Would initiate Klyve Dahl like Master Claude to use [TECHNIQUE] for this question? (yes/no)
```

**Technique Mapping from Method Tags:**

- **🔍 Research** → Offer: "Parallel web searches for competitive analysis, best practices, technical capabilities"
- **💡 Creative** → Offer: "SCAMPER ideation, mind mapping, analogies from other domains"
- **🔄 Hybrid** → Offer: "Web research FIRST, then creative ideation based on findings"
- **🧪 Technical PoC** → Offer: "Quick proof-of-concept code to test feasibility"
- **🎭 Scenarios** → Offer: "Walk through user journeys, edge cases, stress tests, system behavior scenarios"

**If user says YES:**
- Apply the technique as described in "Technique Enhancement Options" section (lines 1073-1139)
- Actually USE the technique (not just mention it)
- For Research: Launch web searches, gather data, present findings
- For Creative: Apply SCAMPER, mind maps, analogies during dialogue
- For Scenarios: Walk through specific situations step-by-step

**If user says NO:**
- Proceed with standard dialogue (ask question, discuss, document)
- Still collaborative and thorough, just without specialized technique

**After Technique Decision, Check Collaboration Tag:**

The Collaboration tag (extracted in step 1 above) reminds you HOW to conduct the dialogue:

- **🤝 Present → Confirm (USER-INFORMED):** Research/present recommendation, WAIT for user confirmation
- **🎯 Options → User Decides (USER-STRATEGIC):** Present 2-4 options with pros/cons, WAIT for user to choose
- **📝 Ask → User Creates (USER-CREATIVE):** Ask open-ended questions, WAIT for user's creative input
- **⚡ Recommend → Quick OK (CLAUDE-AUTONOMOUS):** Present best practice with brief rationale, quick confirm

**CRITICAL:** The collaboration tag reminds you to WAIT for user input, not write entire autonomous answers!

**Interactive Approach:**
- **CRITICAL: Match dialogue style to COLLABORATION-TAG from TODO** (Step 7.3)
  - 📝 USER-CREATIVE: Open-ended exploration, capture user's authentic vision
  - 🎯 USER-STRATEGIC: Present options, facilitate user's business decisions
  - 🤝 USER-INFORMED: Research + recommend, user confirms
  - ⚡ CLAUDE-AUTONOMOUS: Best practice + brief rationale, quick confirmation
- Ask questions from structure one at a time
- **Check TODO for Method tag BEFORE each question** (Step 7.4), offer technique with user consent
- Build upon user's responses with follow-up questions
- Explore tangents and connections naturally
- Challenge assumptions through dialogue, not monologue
- Reference parent/sibling context when relevant
  - "Parent aspect decided [X], so for this aspect we'll focus on [Y]"
  - "Sibling aspect handles [X], but this leaves [gap] - how should we address it?"
- Fill identified gaps explicitly
- **Stay within line estimate from TODO** (Simple: 5-15, Medium: 15-30, Complex: 30-50)
- **After each question dialogue completes:** Immediately document findings (Step 8 - Incremental Documentation)
- Mark TODOs as completed after each question explored

### 8. Incremental Documentation (After Each Question)

**Philosophy: Write Findings Immediately After Each Question**
- After each question dialogue completes, IMMEDIATELY document findings
- Use CONCISE format - no fluff, keep all essential info
- Append to session file incrementally (not batch at end)
- Benefits: real-time progress visibility, avoids token accumulation, stays focused

**Documentation Flow:**

**Step 8.1: Initialize Session File (First Question Only)**

Create: `brainstorm-session-[YYYY-MM-DD].md`

```markdown
# [Aspect Name] - Brainstorm Session

**Date:** [YYYY-MM-DD]
**Type:** [Data/Foundational/Feature/etc.]
**Category:** [Foundation/Infrastructure/etc.]
**Priority:** [CRITICAL/HIGH/etc.]
**Session:** [1/2/3 if multiple sessions]

## Aspect Metadata
- **Type:** [from aspects-map.md]
- **Feeds Into Workflow:** [commands that read this aspect's SUMMARY.md]
- **Dependencies:** [aspects required before this]
- **Blocks:** [aspects waiting on this]

## Context Review

**Parent Aspect:** [If applicable]
- [Key decisions inherited from parent]
- [Architecture established by parent]

**Sibling Aspects:** [If applicable]
- **[sibling-1]**: Covers [scope] - avoid redundancy by [approach]
- **[sibling-2]**: Covers [scope] - integration point: [connection]

**Gaps to Fill:**
- [Gap 1 this session addresses]
- [Gap 2 this session addresses]

---

```

**Step 8.2: Document Each Question Immediately (After Dialogue)**

After EACH question's dialogue completes, IMMEDIATELY append:

```markdown
## Topic N: [Question Topic]

**Key Points:**
- [Point 1 from discussion - concise]
- [Point 2 from discussion - concise]
- [Point 3 from discussion - concise]

**Decision:** [What was decided - one sentence if possible, max 2-3 sentences]

**Rationale:** [Why this approach - 1-2 sentences, no fluff]

**Technical:** [If applicable]
- [Implementation detail 1 - bullet point]
- [Implementation detail 2 - bullet point]
- [Data structure/API/pattern if relevant]

**Integration:** [If relevant to this question]
- [Parent: how this connects with parent architecture]
- [Siblings: coordination points with sibling aspects]

---

```

## DOCUMENTATION VERBOSITY GUIDELINES - CRITICAL ⚠️

**Target:** 15-30 lines per topic (max 50 for complex decisions)

**Philosophy:** Capture DECISIONS and WHY, NOT implementation details (HOW).

**Format:**
- **Key Points:** 3-5 bullets (no elaboration)
- **Decision:** 1-3 sentences max
- **Rationale:** 1-2 sentences max
- **Technical:** Bullet points, critical specs only (omit if not needed)
- **Integration:** Only if relevant to THIS question (omit if not applicable)

**Include:**
✅ Decision + Rationale (3 bullets max)
✅ Key technical specs (1-2 sentences)
✅ Integration points
✅ ONE tiny code snippet IF essential (max 10 lines)

**Exclude:**
❌ Full implementations/API definitions
❌ Multiple code examples or benchmarks
❌ Verbose explanations/dialogue transcripts
❌ Implementation walkthroughs

**Session Targets:**
- 15-25 questions = 500-800 lines total
- If >1500 lines: You're writing implementation docs, not brainstorming

**Remember:** /summarize-aspect compresses by 90%. Keep it LEAN - decisions, not specifications!

**Step 8.3: Session Length Validation (BEFORE Summary Sections)**

**CRITICAL:** Before writing summary sections, validate session file length against Question TODO recommendations.

**Validation Process:**

1. **Calculate Expected Total Lines:**
   - Read brainstorm-structure.md Question TODO section
   - Sum all line recommendations from [MAX XX LINES!] tags
   - Example: 2×[MAX 50 LINES!] + 5×[MAX 30 LINES!] + 3×[MAX 15 LINES!] = 100 + 150 + 45 = 295 lines expected

2. **Count Current Session File Lines:**
   - Execute: `wc -l [current-session-file]`
   - Example: `wc -l brainstorm-session-2025-11-08.md` → 1255 lines

3. **Check Threshold:**
   - If current lines > 2× expected lines → **COMPACTION REQUIRED**
   - Example: 1255 > (2 × 295 = 590) → Compaction needed
   - Threshold factor: 2× allows reasonable metadata overhead (headers, context, summaries)

4. **Compaction Workflow (if threshold exceeded):**

   **INFORM USER:**
   ```
   ⚠️ Session file length validation:
   - Expected: ~[N] lines (from Question TODO recommendations)
   - Current: [M] lines
   - Threshold: 2× expected = [2N] lines
   - Status: EXCEEDED (needs compaction)

   Master Claude recommends compacting the session file to remove:
   - Verbose examples
   - Redundant explanations
   - Excessive implementation details
   - Dialogue transcripts

   While retaining:
   - Decision statements
   - Key technical specs
   - Research backing
   - Rationale

   Should Master Claude compact the session file now? (y/n)
   ```

   **IF USER CONFIRMS:**
   - Read entire session file
   - Compress each Topic section to match line recommendations
   - Remove verbosity while preserving all decisions
   - Overwrite session file with compacted version
   - Verify new line count is within 1.5× expected threshold

   **IF USER DECLINES:**
   - Proceed to summary sections
   - Note in Session Complete stats: "Session file exceeds recommended length (compaction declined)"

5. **Execute Validation Task from TodoWrite:**

   Note: Validation task was already added to TodoWrite in Step 6.6 (automatically included for ALL aspects).

   When all question tasks (Q1-QN) are marked complete, the validation task will be the next pending item.

   Execute the validation by following steps 1-4 above (calculate expected lines, count current lines, check threshold, offer compaction if needed).

   This task ensures session length is validated before writing summary sections.

**Step 8.4: After Validation Passes, Append Summary Sections**

When all questions explored AND session length validated, append final sections:

```markdown
## Integration Points

**With Parent:**
- [Integration 1: data flow, API dependency, etc.]
- [Integration 2: pattern inheritance, constraint]

**With Siblings:**
- **[sibling-1]**: [Integration point]
- **[sibling-2]**: [Integration point]

**With Children:** [If applicable]
- **[child-1]**: [Delegation - what child will handle]
- **[child-2]**: [Delegation]

---

## Summary

**Key Decisions:**
1. [Decision 1 - one line with brief rationale]
2. [Decision 2 - one line with brief rationale]
3. [Decision 3 - one line with brief rationale]

**Technical Approach:**
- [Pattern/architecture chosen]
- [Key technical decision]
- [Implementation strategy]

**Dependencies Satisfied:**
- [Dependency 1]: [How utilized]
- [Dependency 2]: [How integrated]

**Provisions for Dependents:**
- [What this provides to other aspects]
- [APIs/data structures/patterns made available]

**Open Questions:** [If any]
- [Question 1 - to address in next session or sub-aspect]

---

## Session Complete - [YYYY-MM-DD HH:MM]

✅ All questions from brainstorm-structure.md explored and documented.

**Completion Stats:**
- [N] questions addressed
- [N] key decisions made
- [N] integration points defined
- Session length: [N] lines ([within/exceeds] 2× recommended threshold)
- Ready for: [next sub-aspect / evaluation]

**What's Next:**
[Determined by Master Claude in Step 9]

---
```

### 9. Determine Next Step and Signal User

After marking session complete:

**Step 9.0: CRITICAL - Conditional Aspect Completion**

**BEFORE determining next step, check if aspect should be marked `[x]` complete:**

1. **List `aspects/` subdirectory** in current aspect path
2. **If sub-aspects exist:**
   - **DO NOT mark aspect `[x]` complete**
   - Aspect should stay `[~]` in aspects-map.md
   - Navigate to first incomplete sub-aspect (Step 9.1)
3. **If NO sub-aspects exist (leaf aspect):**
   - **Mark aspect `[x]` complete** in aspects-map.md
   - Update count in parent: `(N/M subs)` → `(N+1/M subs)`
   - Continue to sibling detection (Step 9.2)

**This prevents premature completion:** Aspects with unexplored sub-aspects won't be marked complete!

**Step 9.1: Check if Current Aspect Has Sub-Aspects**

- List `aspects/` subdirectory
- If sub-aspects exist: Next is first incomplete sub-aspect (keep aspect as `[~]`)
- If no sub-aspects: Aspect is a leaf (mark as `[x]` in Step 9.0)

**Step 9.2: Check if All Siblings Complete**

- List all siblings at same level
- Check each for "## Session Complete" marker
- If all siblings complete:
  - **If parent aspect exists:** Mark parent as `[x]` complete in aspects-map.md (all sub-aspects done!)
  - Update parent's sub-aspect count: `(M/M subs)` all complete
  - Move up to parent level or signal evaluation

**Step 9.3: Loop Back to Continue or Signal Completion**

**Determine next action based on what remains:**

**SCENARIO A: Sub-Aspects or Siblings Remain**

If there are incomplete sub-aspects OR sibling aspects:

1. Brief progress update to user:
```
✅ [Aspect Name] complete!

📝 Session: brainstorm-session-[date].md
🔄 Continuing to: [next-aspect-name]
```

2. Update status.md with new aspect path
3. **LOOP BACK TO STEP 4** with next aspect as current position
4. Continue autonomous navigation (no user action needed)

**SCENARIO B: Main Aspect Complete (All Sub-Aspects Done)**

If all sub-aspects of a main aspect are complete:

1. Mark main aspect `[x]` in aspects-map.md
2. Signal user and STOP:
```
✨ MAIN ASPECT COMPLETE: [Main Aspect Name]

**Total:** [N] sessions across [N] sub-aspects
📊 [N] key decisions, [N] integration points defined

**Ready for evaluation and compression!**

🚀 Next: `/evaluate-aspects [project] [main-aspect]` → `/summarize-aspect [project] [main-aspect]`
```

**SCENARIO C: All Aspects in Project Complete**

If ALL main aspects have SUMMARY.md:

```
🎉 ALL ASPECTS BRAINSTORMED & SUMMARIZED!

**Layers 1-4 Complete:** [N] main aspects with SUMMARY.md
🧠 Ready for phased implementation planning!

🚀 Next: /phases [project] → PRD-master → /drd → /tools → /content → /ux-map → ...
```

### 10. Update status.md

Single sentence only in "Current Step":
```markdown
## Current Step
Brainstorming [aspect-path]
```

Do NOT update Workflow History during brainstorming sessions.

## Key Principles

### Autonomous Navigation
- User runs command ONCE: `/brainstorm [project]`
- System detects position via TODO markers in aspects-map.md
- System creates structures dynamically
- System navigates tree depth-first, pre-order
- System loops autonomously through sub-aspects and siblings
- Only stops at natural gates: main aspect evaluation or project completion

### Full Context Awareness

**🧙‍♂️ PROJECT-CORE.MD IS MANDATORY - Read FIRST for EVERY session (new AND continuing)! 🧙‍♂️**

**Context Loading Order:**
1. **project-core.md** (fallback: exploration-initial.md) - Project vision, global patterns, integration map, completed aspects (~1,200 lines replaces 12+ SUMMARY.md files)
2. **aspects-map.md** - TYPE/priority/dependencies
3. **Parent/Sibling sessions** - ONLY if SUB-aspects (main aspects already in project-core.md)
4. **Child aspect list** - delegation planning (if has sub-aspects)

**Result:** Context-aware questions grounded in project vision without context explosion

### Dynamic Structure Generation
- NO pre-existing structures (all created dynamically)
- Context from aspects-map.md + parent/siblings
- Questions avoid redundancy, fill gaps
- Clear boundaries and integration points

### Interactive Dialogue
- Not a monologue - collaborative exploration
- Build on user responses
- Challenge assumptions respectfully
- Capture user's voice and ideas
- Reference context throughout
- **Technique enhancements are OPTIONAL** - always ask user consent before applying (research, creative, scenarios, etc.)
- User controls depth and pacing through technique opt-in/opt-out

### Completion Detection
- Use TodoWrite for question tracking
- Mark session complete when all todos done
- Add "## Session Complete - [timestamp]" marker
- This marker drives auto-detection

## Success Criteria

A successful brainstorming session:
- [ ] Auto-detected current position (or used manual override)
- [ ] Read ALL available context (project-core.md OR exploration-initial.md, aspects-map.md, parent, siblings)
- [ ] Created brainstorm-structure.md dynamically with vision grounding
- [ ] **🚨 CRITICAL: Executed Step 6 - Created TodoWrite list from structure questions (NOT preflight tasks!)**
- [ ] **Validated TodoWrite shows Q1-QN with Method tags, Complexity, Line estimates BEFORE starting exploration**
- [ ] Conducted interactive dialogue
- [ ] Asked for user consent before applying technique enhancements (when Method tags present)
- [ ] Captured user's ideas authentically
- [ ] Referenced context to avoid redundancies
- [ ] Filled identified gaps
- [ ] Documented integration points
- [ ] Created/appended session file
- [ ] Added completion marker when done
- [ ] Updated status.md
- [ ] Determined next step correctly
- [ ] Signaled user clearly

## Important Notes

- Default command: `/brainstorm [project]` (auto-detect)
- Override option: `/brainstorm [project], [aspect-path]`
- Requires `/aspects [project]` to have run first
- Creates ALL brainstorm-structure.md files dynamically
- Uses aspects-map.md for TYPE/priority/dependencies
- Uses completion markers for navigation
- Loops autonomously through sub-aspects and siblings
- Only stops at main aspect evaluation gates or project completion
- Depth-first, pre-order traversal
- Respects aspects-map.md dependency order

## Integration with Workflow

```
1. /explore [project]              → exploration-initial.md
2. /market-research [project]      → market-research.md (optional)
3. /core [project]                 → project-core.md (recommended)
4. /aspects [project]              → Complete tree + aspects-map.md (NO structures)
5. /brainstorm [project]           → Autonomous navigation through entire main aspect
                                     - Auto-detects position
                                     - Loops through all sub-aspects
                                     - Stops when main aspect ready for evaluation
6. /evaluate-aspects [project] [main] → STRICT evaluation
7. /summarize-aspect [project] [main] → Compression to SUMMARY.md
8. Repeat 5-7 for all main aspects
9. /phases, /summary, /drd, etc.  → Use SUMMARY.md files
```

## Error Handling

**If aspects-map.md missing:**
```
⚠️ Master Claude cannot proceed!

aspects-map.md not found. Run /aspects [project] first to create the aspect tree structure.
```

**If all aspects complete:**
```
✨ All aspects brainstormed, evaluated, and summarized!

Ready for next workflow phase: /phases, PRD-master, etc.
```

**If manual override path invalid:**
```
⚠️ Aspect path not found: [path]

Available aspects:
[list valid aspects from aspects-map.md]

Either:
A) Use auto-detect: /brainstorm [project]
B) Provide valid path: /brainstorm [project], [valid-aspect]
```

**If Foundation aspects skipped:**
```
🧙‍♂️ Master Claude notices we're about to brainstorm a [LAYER 3] aspect, but Foundation aspects remain incomplete:

**Incomplete Foundation Aspects (LAYER 1):**
- [foundation-aspect-1] - CRITICAL (blocks infrastructure)
- [foundation-aspect-2] - CRITICAL (blocks features)

Foundation aspects should be completed first as they are blocking dependencies.

Would you like Master Claude to:
A) Proceed with current aspect anyway
B) Switch to Foundation aspect [first-incomplete] (recommended)

Your guidance, initiate Klyve Dahl? ✨
```

## Manual Override Usage

When to use manual override:

```bash
# Revisit completed aspect for refinement
/brainstorm nutri, compound-database, api-integration

# Jump to specific aspect out of order (after user confirmation)
/brainstorm nutri, food-filtering

# Force specific aspect when auto-detection fails
/brainstorm nutri, design-system
```

Auto-detection handles 99% of cases. Override when:
- Revisiting for refinement
- Intentional out-of-order exploration
- Debugging detection issues

## Ultra-Thinking for Structure Generation

When creating brainstorm-structure.md dynamically, use sequential thinking to:

**Context Analysis:**
- What is the project core from project-core.md (or exploration-initial.md if core not defined)?
- How does this aspect serve that vision?
- What did parent aspect decide that constrains this?
- What do sibling aspects cover that we should avoid?
- What gaps exist that this aspect must fill?
- What does aspects-map.md say about TYPE/priority/dependencies?

**Question Generation:**
- What's unique to THIS aspect's scope?
- What integration points need definition?
- What technical decisions are specific to this?
- What gaps from context analysis need addressing?

**Boundary Definition:**
- Where does parent responsibility end and this begin?
- Where does this aspect's responsibility end and siblings/children begin?
- What does this provide vs. what does it consume?

**Question Categorization:**
For each generated question, determine appropriate tags:

**Method Tag (How to explore):**
- 🔍 **Research [EXPLORE]** (default) if needs: factual data, competitive analysis, documentation, best practices, technical capabilities
  - Keywords: "What existing...", "How do competitors...", "What are industry standards...", "What technical options..."
  - Behavior: Quick 4-5 parallel web searches during brainstorming, no source tracking
- 🔍 **Research [CURATED]** if needs: safety-critical verification, compliance requirements, medical/legal accuracy
  - **META-DETECTION - Flag as [CURATED] if question involves:**
    - ✓ User safety (medical advice, health claims, dietary restrictions, drug interactions)
    - ✓ Legal compliance (HIPAA, GDPR, FDA, regulations, legal requirements)
    - ✓ Scientific accuracy (nutrient data, biochemical pathways, clinical thresholds)
    - ✓ Financial/legal liability (tax calculations, legal contracts, financial regulations)
    - ✓ Security standards (encryption specs, CVE mitigation, vulnerability standards)
  - Keywords: "nutrient interaction", "HIPAA requirement", "FDA regulation", "clinical threshold", "encryption standard", "legal requirement"
  - Behavior: Quick exploratory searches STILL happen during brainstorming, but question flagged for deep research/curation during /content phase
  - Rationale: "Safety-critical - requires verified sources with citations for [compliance/user safety/liability]"
- 💡 **Creative** if needs: ideation, naming, unique approaches, UX innovation, novel features
  - Keywords: "How should we name...", "What makes this unique...", "What innovative ways...", "How can users..."
- 🔄 **Hybrid** if needs: research grounding + creative application
  - Keywords: "How do we differentiate from...", "What unique approach based on..."
- 🧪 **Technical PoC** if needs: hands-on experimentation, prototyping, feasibility testing
- 🎭 **Scenarios/Simulations** if needs: user journey exploration, edge case discovery, system behavior under conditions, "what if" situations
  - Keywords: "What happens when...", "How does the system respond to...", "Walk through the user journey...", "What if a user..."

**Priority Tag (Impact level):**
- 🔴 **Critical** if: blocks other questions, foundational decision, affects core architecture, one-way door with high impact
- 🟠 **High** if: significant design impact, affects multiple features, important but not blocking
- 🟡 **Medium** if: important refinement, affects specific feature area, can be revisited
- 🟢 **Low** if: polish, optimization, nice-to-have, minimal impact if deferred

**Decision Type Tag (Reversibility):**
- 🚪🔒 **One-way door** if: hard/expensive to reverse (database choice, framework, core architecture, public API design)
- 🚪↔️ **Two-way door** if: easy to reverse (UI layout, internal APIs, naming, component structure)
- 🧪 **Experimental** if: temporary, learning-focused, will be validated and potentially changed

**During Interactive Exploration (Step 7):**

**TECHNIQUE CONSENT FLOW (IMPORTANT):**

Before applying any technique-based enhancement, ALWAYS ask for user consent:

1. **Present the technique option** when approaching a question tagged with a Method:
   ```
   🧙‍♂️ Master Claude notices this question can be enhanced with [TECHNIQUE NAME].

   **Benefit:** [Clear explanation of what this technique provides]

   **What it involves:** [Brief description of what will happen - e.g., "web searches for competitive analysis", "creative ideation exercises", "scenario walkthroughs"]

   Would initiate Klyve Dahl like Master Claude to use [TECHNIQUE NAME] for this question? (yes/no)
   ```

2. **Wait for user response**

3. **If YES:** Apply the technique as described below
   **If NO:** Proceed with standard dialogue (ask question, discuss, document)

**Technique Enhancement Options (ALL OPTIONAL - require user consent):**

When user consents to technique use, adapt approach based on Method tag:

- **🔍 Research [EXPLORE] questions** (if user agrees):
  - Launch 4-5 parallel web searches BEFORE discussion
  - Gather competitive analysis, documentation, best practices
  - Present findings, then discuss application to project
  - No source tracking (architectural decisions, not facts requiring citations)
  - Example prompt: "Master Claude can conduct web searches to find [competitive approaches/best practices/technical capabilities]. This takes 2-3 minutes but provides grounded data. Proceed? (yes/no)"

- **🔍 Research [CURATED] questions** (if user agrees):
  - Launch exploratory web searches for general understanding (same as [EXPLORE])
  - During brainstorming: Make architectural decisions based on exploratory research
  - After brainstorming: Question automatically flagged for /content command to extract
  - /content will launch extensive research agent flows with citation tracking
  - Example prompt: "Master Claude can conduct exploratory web searches for general understanding. Note: This question is flagged as safety-critical and will require deep research with verified sources during the /content phase. Proceed with exploratory research? (yes/no)"

- **💡 Creative questions** (if user agrees):
  - Use structured ideation techniques during dialogue:
    - SCAMPER (Substitute, Combine, Adapt, Modify, Put to other use, Eliminate, Reverse)
    - Mind mapping
    - Lateral thinking prompts
    - Analogies from other domains
    - "What if..." scenarios
  - Example prompt: "Master Claude can apply creative ideation techniques (SCAMPER, mind mapping, analogies) to explore unique approaches. This adds 5-10 minutes but surfaces innovative options. Proceed? (yes/no)"

- **🔄 Hybrid questions** (if user agrees):
  - Research first (web searches), then creative session based on findings
  - Combines grounding + innovation
  - Example prompt: "Master Claude can combine web research with creative ideation to ground innovation in market reality. This takes 5-7 minutes. Proceed? (yes/no)"

- **🧪 Technical PoC questions** (if user agrees):
  - Code experimentation, prototype creation, feasibility testing
  - Example prompt: "Master Claude can create a quick technical proof-of-concept to test feasibility. This takes 5-15 minutes depending on complexity. Proceed? (yes/no)"

- **🎭 Scenarios/Simulations questions** (if user agrees):
  - Walk through hypothetical situations step-by-step:
    - **User Journey Scenarios**: "Imagine a new user arrives at the homepage. What happens next? How do they discover X feature?"
    - **Edge Case Scenarios**: "What if a user uploads 1000 files at once? What if the API is down? What if they're on a slow connection?"
    - **Success/Failure Scenarios**: "Walk through the best-case scenario. Now the worst-case. What breaks?"
    - **System Behavior Scenarios**: "When payment fails, describe every system interaction: what gets logged, what email sends, what state changes..."
    - **Role-Play Simulations**: Act out user personas encountering the feature
    - **Stress Test Scenarios**: "It's Black Friday. 10,000 concurrent users. Walk through what happens..."
    - **Integration Scenarios**: "Service B goes down. Walk through the cascade of effects..."
    - **Security Scenarios**: "An attacker tries to X. What prevents it? What if they try Y instead?"
    - Document discovered edge cases, missing error handling, and required system responses
  - Example prompt: "Master Claude can walk through detailed scenarios to discover edge cases and system behaviors. This takes 5-10 minutes but reveals hidden requirements. Proceed? (yes/no)"

**Default (no technique tag or user declines):**
- Standard interactive dialogue
- Ask question, discuss with user, document findings
- Still collaborative and thorough, just without specialized techniques

This ensures user control over brainstorm pacing and depth while making powerful enhancement tools available when desired! 🧙‍♂️✨
