---
description: Generate comprehensive summary of an aspect including ALL sub-aspects at ANY depth
argument-hint: [project-name] [aspect-name]
---

# Summarize Aspect Command - Recursive Compression

## Objective
Create a single comprehensive SUMMARY.md for a top-level aspect that captures ALL decisions, technical details, and key information from every sub-aspect, sub-sub-aspect, and deeper nested aspects - recursively to infinite depth.

## Philosophy
**Compression Without Loss:**
- Transform EXPLORATORY brainstorming (the journey) into DECLARATIVE summaries (the destination)
- Preserve ALL final decisions, technical specs, numbers, and action items
- Compress discussion, alternatives, and exploration process
- 90% context reduction, 0% information loss

**Recursive Completeness:**
- ONE summary per top-level aspect
- Captures EVERYTHING beneath it, no matter how deep
- Hierarchical structure preserves parent-child relationships
- Downstream commands read ONE file, get complete picture

## Process

**IMPORTANT:** Do NOT ultrathink when starting this command. The instructions are clear. Only ultrathink during Step 4 (Compression Strategy) when analyzing brainstorm content.

**TODO List Integration:**

**WHEN TO CREATE:** Immediately after parsing arguments (step 1 begins), create a TODO list to track progress through the 8-step workflow.

**WHY:** This command has multiple distinct steps that take time. The TODO list provides transparency and helps the user understand workflow progress.

**INITIAL TODO LIST:**
```typescript
TodoWrite({
  todos: [
    { content: "Parse and validate arguments", status: "in_progress", activeForm: "Parsing and validating arguments" },
    { content: "Discover brainstorm files recursively", status: "pending", activeForm: "Discovering brainstorm files recursively" },
    { content: "Read all discovered brainstorm files", status: "pending", activeForm: "Reading all discovered brainstorm files" },
    { content: "Analyze content and plan compression strategy", status: "pending", activeForm: "Analyzing content and planning compression strategy" },
    { content: "Generate SUMMARY.md with hierarchical structure", status: "pending", activeForm: "Generating SUMMARY.md with hierarchical structure" },
    { content: "Save output and update status.md", status: "pending", activeForm: "Saving output and updating status.md" },
    { content: "Validate completeness and generate report", status: "pending", activeForm: "Validating completeness and generating report" },
    { content: "Generate ultra-compressed project-core.md entry", status: "pending", activeForm: "Generating ultra-compressed project-core.md entry" }
  ]
});
```

**UPDATE PATTERN:** Mark each step `completed` IMMEDIATELY after finishing it, and mark the next step `in_progress` BEFORE starting work on it. This keeps the user informed of current progress.

### 1. Parse and Validate
```bash
/summarize-aspect [project-name] [aspect-name]

# Examples:
/summarize-aspect nutri compound-database
/summarize-aspect nutri food-filtering
/summarize-aspect nutri personalization-engine
```

- Extract project name and aspect name from arguments
- Verify project exists at `/Projects/[project-name]/`
- Verify aspect folder exists at `.wiz/exploration/aspects/[aspect-name]/`
- Confirm aspect has brainstorm files (direct or nested)

**After validation:** Mark step 1 `completed`, mark step 2 `in_progress`.

### 2. Recursive Discovery Phase

**CRITICAL: You must discover ALL brainstorm files at ANY depth!**

Use recursive traversal to find every brainstorm file:

```
Starting point: .wiz/exploration/aspects/[aspect-name]/

1. Check current level for brainstorm-session-*.md files
2. Look for aspects/ subfolder
3. If aspects/ exists:
   - List all subdirectories
   - For EACH subdirectory:
     - RECURSE (go to step 1 with new path)
4. Continue until no more aspects/ subfolders found
```

**Example for compound-database:**
```
Found: aspects/api-integration/brainstorm-session-2025-01-14.md (depth 1)
Found: aspects/factor-engine/brainstorm-session-2025-01-14.md (depth 1)
Found: aspects/advanced-compounds/brainstorm-session-2025-01-14.md (depth 1)
  Recurse into: aspects/advanced-compounds/aspects/
    Found: phytochemicals/brainstorm-session.md (depth 2)
      Recurse into: phytochemicals/aspects/
        Found: flavonoids/brainstorm.md (depth 3)
    Found: contaminants/brainstorm-session.md (depth 2)
Found: aspects/quality-validation/brainstorm-session-2025-01-14.md (depth 1)
Found: aspects/presentation-layers/brainstorm-session-2025-01-14.md (depth 1)
Found: aspects/compound-interactions/brainstorm-session-2025-01-14.md (depth 1)

Total discovered: 9 brainstorm files
Maximum depth: 3 levels
```

**Build hierarchical map:**
```javascript
{
  "api-integration": { depth: 1, file: "...", children: [] },
  "factor-engine": { depth: 1, file: "...", children: [] },
  "advanced-compounds": {
    depth: 1,
    file: "...",
    children: [
      {
        "phytochemicals": {
          depth: 2,
          file: "...",
          children: [
            { "flavonoids": { depth: 3, file: "..." } }
          ]
        }
      },
      { "contaminants": { depth: 2, file: "..." } }
    ]
  },
  // ... etc
}
```

**After discovery:** Mark step 2 `completed`, mark step 3 `in_progress`. Update step 3 content to include file count: "Read all discovered brainstorm files (N files)".

### 3. Read Phase

Read ALL discovered brainstorm files:
- Read in order (depth-first)
- Track which file belongs to which aspect/sub-aspect
- Preserve hierarchical relationships

**After reading:** Mark step 3 `completed`, mark step 4 `in_progress`.

### 4. Compression Strategy

**NOW ULTRATHINK:** Use `mcp__sequential-thinking__sequentialthinking` to analyze all brainstorm content and plan the compression approach.

**For EACH brainstorm file, extract:**

✅ **KEEP VERBATIM:**
- Final decisions (what was decided)
- Technical specifications (schemas, APIs, tables, fields)
- All numbers ($0/month, 100-500 interactions, 3,702 lines, percentages)
- Scopes (what's in Phase 1, what's deferred)
- Cost analysis
- Action items

📦 **COMPRESS:**
- Options considered → "Evaluated 5 approaches"
- Discussion text → Core reasoning only (2-5 lines)
- Examples → Keep 1-2 key examples, reference the rest
- Alternatives rejected → "Rejected X because Y" (1 line each)

🗑️ **DROP:**
- Repeated/redundant information
- Meta-commentary ("Let me think...", "Should we consider...")
- Play-by-play of exploration
- Extensive examples when 1-2 demonstrate the point
- Process discussions (keep conclusions only)

**Structured extraction per sub-aspect:**

```markdown
## SUB-ASPECT: [Name]

**Decision:** [What was decided - 2-3 lines]

**Rationale:** [Why - core reasoning only - 2-3 lines]

**Technical:** [Schemas, numbers, specifics - 3-5 lines]
- Database tables, fields, types
- API endpoints
- Algorithms chosen
- Data structures

**Cost:** [$X/month or timeline]

**Impact:** [What this enables - 1-2 lines]

**Example:**
[1 key example showing decision in action - 3-5 lines]

**Full Detail:** [relative path to full brainstorm file]
```

**Compression target:** 15-30 lines per sub-aspect (down from 300-800 lines)

**After compression analysis:** Mark step 4 `completed`, mark step 5 `in_progress`.

### 5. Generate SUMMARY.md

Create summary with hierarchical structure:

```markdown
# [Aspect Name] - Aspect Summary

*This summary covers [N] sub-aspects with [N] additional nested layers*

## Overview
[2-3 paragraph high-level description of entire aspect]

## Core Philosophy
["Quote key philosophy" if applicable]

---

## SUB-ASPECT 1: [Name]

**Decision:** ...
**Rationale:** ...
**Technical:** ...
**Cost:** ...
**Impact:** ...
**Example:** ...

**Full Detail:** aspects/[name]/brainstorm-session-2025-01-14.md

---

## SUB-ASPECT 2: [Name]

[Same structure]

---

## SUB-ASPECT 3: [Name with nested children]

**Decision:** ...
**Rationale:** ...
[etc]

### SUB-SUB-ASPECT 3.1: [Nested Name]

**Decision:** ...
**Rationale:** ...
**Technical:** ...
**Cost:** ...
**Impact:** ...

**Full Detail:** aspects/[parent]/aspects/[name]/brainstorm-session.md

#### SUB-SUB-SUB-ASPECT 3.1.1: [Even Deeper]

**Decision:** ...
**Rationale:** ...

**Full Detail:** aspects/[parent]/aspects/[child]/aspects/[name]/brainstorm.md

---

## Consolidated Technical Architecture

[Unified view of ALL technical decisions across ALL sub-aspects]

**Database Schema:**
- [Tables from all sub-aspects]

**APIs & Integrations:**
- [APIs from all sub-aspects]

**UI Components:**
- [Components from all sub-aspects]

**Algorithms & Logic:**
- [Key algorithms from all sub-aspects]

---

## Consolidated Cost Analysis

| Component | Phase 1 | Phase 2 | Phase 3+ |
|-----------|---------|---------|----------|
| [Item 1]  | $X      | $Y      | $Z       |
| [Item 2]  | $X      | $Y      | $Z       |
| **TOTAL** | **$X**  | **$Y**  | **$Z**   |

---

## Consolidated Action Items

### Immediate (Pre-Development)
- [ ] [Action from sub-aspect 1]
- [ ] [Action from sub-aspect 2]

### Phase 1 Development
- [ ] [Action from sub-aspect 3]
- [ ] [Action from sub-aspect 4]

### Phase 2 Enhancement
- [ ] [Action from sub-aspect 5]

---

## Coverage Map

*Visual representation of what was summarized:*

- ✓ [Sub-Aspect 1] (1 brainstorm file)
- ✓ [Sub-Aspect 2] (1 brainstorm file)
- ✓ [Sub-Aspect 3] (1 brainstorm file)
  - ✓ [Sub-Sub-Aspect 3.1] (1 brainstorm file)
    - ✓ [Sub-Sub-Sub-Aspect 3.1.1] (1 brainstorm file)
  - ✓ [Sub-Sub-Aspect 3.2] (1 brainstorm file)
- ✓ [Sub-Aspect 4] (1 brainstorm file)
- ✓ [Sub-Aspect 5] (1 brainstorm file)
- ✓ [Sub-Aspect 6] (1 brainstorm file)

**Total Brainstorm Files Summarized:** [N]
**Maximum Nesting Depth:** [N] levels
**Original Total Lines:** ~[N]
**Summary Lines:** ~[N]
**Compression Ratio:** [N]:1

---

## Reference Links

All detailed brainstorming sessions remain available at:
- [List all paths to full brainstorm files]
```

**After generating SUMMARY.md:** Mark step 5 `completed`, mark step 6 `in_progress`.

### 6. Save Output

- Write SUMMARY.md to `.wiz/exploration/aspects/[aspect-name]/SUMMARY.md`
- Preserve all original brainstorm files (DO NOT move or delete them)
- Update status.md with completion note

**After saving:** Mark step 6 `completed`, mark step 7 `in_progress`.

### 7. Validation & Reporting

Before finalizing, validate:
- [ ] All discovered brainstorm files are represented in summary
- [ ] Hierarchical structure preserved (heading levels match depth)
- [ ] All technical specifics included (schemas, numbers, costs)
- [ ] All final decisions captured
- [ ] Coverage map shows complete tree
- [ ] Compression ratio documented

Report to user:
```
✅ Summarized [aspect-name] aspect

📊 Discovery Results:
- Total brainstorm files found: [N]
- Maximum nesting depth: [N] levels
- Hierarchical structure: [tree diagram]

📄 Compression Results:
- Original lines: ~[N]
- Summary lines: ~[N]
- Compression ratio: [N]:1
- Information loss: 0%

💾 Output saved to:
- .wiz/exploration/aspects/[aspect-name]/SUMMARY.md

🔗 Original brainstorms preserved at:
- [List all paths]

✨ Downstream commands (/phases, /summary, prd-generator) can now read this ONE file instead of [N] files!
```

**After validation and reporting:** Mark step 7 `completed`, mark step 8 `in_progress`.

### 8. Generate Ultra-Compressed project-core.md Entry

**CRITICAL:** After completing SUMMARY.md, extract an ultra-compressed entry (~80 lines) for project-core.md to enable cross-aspect context without context window explosion.

**Extract from SUMMARY.md:**

✅ **INCLUDE (numbers & integration contracts):**
- Core decisions with numbers (280 compounds, $26.8K budget, 4-layer confidence, 18 niche conditions)
- Architectural patterns (UUID mapping, multi-source aggregation formulas, progressive disclosure)
- Sub-aspects list (name + 1-line decision each)
- Integration contracts (Provides/Consumes - what other aspects need/use)
- Key tables/entities (names only, not full schemas)
- Data sources (list, not detailed specs)

❌ **EXCLUDE (keep in SUMMARY.md for PRD/DRD):**
- Market sizing & competitive analysis ("80M+ underserved users", "14/18 conditions ZERO competitors")
- Revenue projections & business metrics ($400K conservative, conversion rates, profit margins)
- Detailed rationale/WHY explanations (keep WHAT decisions)
- User examples & scenarios ("User logs spinach → Dashboard shows...")
- Full schemas/algorithms/formulas (keep high-level only)
- Detailed category breakdowns (keep counts, not full lists)
- Action items (keep for /phases)
- UI/UX detailed flows (keep for /ux-map)
- Meta information (Coverage Map, Reference Links, compression stats)

**Format Template:**
```markdown
## ASPECT [NN]: [aspect-name]

**Status:** ✅ Complete (YYYY-MM-DD) | **Budget:** $XX-YYK pre-launch, $XK/yr

**Core Decisions:**
- [Number-driven decision 1]
- [Architectural pattern decision 2]
- [Data sourcing decision 3]
- [Key technical approach 4]
- [Integration strategy 5]

**Sub-Aspects ([N] total):**
1. **sub-1:** [1-line decision]
2. **sub-2:** [1-line decision]
   - **nested:** [1-line decision]
3. **sub-3:** [1-line decision]

**Integration Contracts:**
- **Provides:** [Object/pattern/API names other aspects consume]
- **Consumes:** [Dependencies from other aspects]

**Key Tables/Entities:** [table1, table2, table3, ...]

**Data Sources:** [Source1 (API), Source2 (bulk), Source3 (manual)]

**Full Detail:** [SUMMARY.md](exploration/aspects/[NN]-[aspect-name]/SUMMARY.md) ([XXX] lines, [N]:1 compression from [XXXX] original)
```

**Target:** 70-90 lines per aspect entry

**Display to User:**
```
🎯 Ultra-Compressed Entry Generated (~[N] lines)

Should Master Claude append this to project-core.md?
- This enables /brainstorm to read ONE file (~1,200 lines for 13 aspects)
- Instead of 12+ SUMMARY.md files (12,000+ lines)
- Solves context window explosion problem

Options:
[y] Append to project-core.md automatically
[n] Show me the entry first (I'll add it manually)
[s] Skip (keep it manual for now)
```

**If user approves ([y]):**
1. Read current project-core.md
2. Append ultra-compressed entry
3. Update "Aspects Completed" counter at top
4. Update Integration Map if new dependencies discovered
5. Update Appendix: Quick Reference with new totals
6. Save project-core.md

**Report:**
```
✅ project-core.md updated!

📊 Compression:
- SUMMARY.md: [XXX] lines (Tier 2)
- project-core entry: [YY] lines (Tier 3)
- Compression: [N]:1 from original brainstorms

💾 Saved to:
- .wiz/project-core.md

🎯 Impact:
- After 13 aspects: project-core.md will be ~1,200 lines total
- /brainstorm can read entire project context without blowing context window!
```

**After completing step 8:** Mark step 8 `completed`. All tasks complete!

## Compression Guidelines

### Decision Extraction Template

For each Topic/Sub-Topic in brainstorm:

**IF Topic has Decision section:**
```
Original: 100 lines of discussion + options + decision + rationale
Summary:
  Decision: [Final choice - 1 line]
  Rationale: [Why - 2-3 core reasons]
  Technical: [Specifics - 3-5 lines]
```

**IF Topic discusses alternatives:**
```
Original: "We considered A (pros..., cons...), B (pros..., cons...), C..."
Summary: "Evaluated 3 approaches (A, B, C). Selected B for [key reason]."
```

**IF Topic has examples:**
```
Original: 5-10 detailed examples
Summary: 1-2 representative examples + "See full detail for additional examples"
```

**IF Topic has technical specs:**
```
PRESERVE VERBATIM: All schemas, tables, fields, types, APIs, numbers
```

### Hierarchy Preservation

Use markdown heading levels to show nesting:
- `##` = Sub-aspect (depth 1)
- `###` = Sub-sub-aspect (depth 2)
- `####` = Sub-sub-sub-aspect (depth 3)
- `#####` = Deeper (depth 4+)

**Visual indentation in coverage map:**
```
- ✓ Parent
  - ✓ Child
    - ✓ Grandchild
      - ✓ Great-grandchild
```

## Usage Examples

```bash
# Summarize Nutri's compound database aspect (6 sub-aspects)
/summarize-aspect nutri compound-database

# Summarize food filtering aspect
/summarize-aspect nutri food-filtering

# Summarize personalization engine
/summarize-aspect nutri personalization-engine

# Run for all 10 aspects (one at a time)
/summarize-aspect nutri compound-database
/summarize-aspect nutri food-filtering
/summarize-aspect nutri personalization-engine
/summarize-aspect nutri user-profiling-onboarding
/summarize-aspect nutri intelligent-recommendations
/summarize-aspect nutri multi-user-platforms
/summarize-aspect nutri data-integration
/summarize-aspect nutri tracking-analytics
/summarize-aspect nutri security-privacy
/summarize-aspect nutri platform-infrastructure
```

## Integration with Workflow

**After summarization, update downstream commands to read summaries:**

### 1. `/phases` Command
**Current:** Reads all brainstorm-session-*.md files
**Updated:** Reads SUMMARY.md files only

### 2. `/summary` Command
**Current:** Reads all brainstorm-session-*.md files
**Updated:** Reads SUMMARY.md files only

### 3. `prd-generator` Agent
**Current:** Reads all brainstorm-session-*.md files
**Updated:** Reads SUMMARY.md files only (with option to selectively read full brainstorms for specific phase details)

## Success Criteria

A successful aspect summarization:
- [ ] Discovers ALL brainstorm files recursively (any depth)
- [ ] Builds accurate hierarchical map
- [ ] Preserves ALL final decisions verbatim
- [ ] Preserves ALL technical specifications (schemas, APIs, numbers)
- [ ] Compresses discussion/exploration appropriately
- [ ] Maintains parent-child relationships in structure
- [ ] Includes coverage map showing complete tree
- [ ] Achieves 8:1 to 12:1 compression ratio
- [ ] Zero information loss on key decisions
- [ ] Links to all full brainstorm files for reference
- [ ] Validates completeness before finalizing

## Important Notes

- Run this command AFTER completing all brainstorming for an aspect
- One command per top-level aspect (processes all sub-aspects automatically)
- Original brainstorm files are NEVER modified or deleted
- Summary enables 75-80% context reduction across workflow
- Can regenerate summary if brainstorms are updated
- Downstream commands get complete picture from ONE file
- Scales to any nesting depth (2, 3, 10+ levels - works the same)

## Expected Results for Nutri

| Aspect | Sub-Aspects | Original Lines | Summary Lines | Ratio |
|--------|-------------|----------------|---------------|-------|
| Compound Database | 6 | 3,702 | ~350 | 10.5:1 |
| Food Filtering | 8 | ~800 | ~100 | 8:1 |
| Personalization Engine | ~5 | ~600 | ~80 | 7.5:1 |
| ... (7 more aspects) | ~40 total | ~4,000 | ~500 | 8:1 |
| **TOTAL** | **~60** | **~9,000** | **~1,000** | **9:1** |

**Context saved across workflow (4 consumers × reduced lines):**
- Before: 9,000 lines × 4 = 36,000 tokens
- After: 1,000 lines × 4 = 4,000 tokens
- **Reduction: 89%** 🎯✨
