---
description: Interactive aspect tree creation with 3 approval gates for collaborative planning
argument-hint: [project-name]
---

# Aspects Analysis Command - Interactive Tree Generation with 3 Approval Gates

## Objective
Collaboratively create the ENTIRE aspect tree structure through 3 interactive approval gates, using EXTENSIVE ultra-thinking to categorize aspects by TYPE, determine dependencies, and establish optimal brainstorming order. User validates scope at each gate to ensure comprehensive coverage before folder creation.

**CRITICAL:** This is pure structural analysis - create ONLY:
1. Empty folder structure (to ANY depth needed)
2. aspects-map.md with complete TYPE metadata and dependency graph

**NO brainstorm-structure.md files are created** - those are generated dynamically by /brainstorm command.

**NO SCOPE LIMITATIONS:** Do not worry about:
- Number of aspects (could be 5 or 500)
- Tree depth (go as deep as needed - 2, 3, 4, 5+ levels, whatever is required)
- Time to brainstorm (not this command's concern)
- Complexity (embrace full scope for one-shot vibecoding)

The ONLY job is to create the complete tree structure that represents the FULL project scope.

## Philosophy

**Interactive Collaborative Planning:**
- **3 Approval Gates** ensure user validates scope at critical decision points
- **Early gap detection** - Find missing aspects at Gate 1 vs mid-brainstorm
- **Appropriate depth** - Validate sub-aspect breakdown at Gate 2
- **Confident execution** - User ready to proceed after Gate 3
- **User expertise injection** - Domain knowledge shapes the structure

**Structure First, Context Later:**
- Create complete folder tree upfront (all depths)
- NO brainstorm-structure.md files created (moved to /brainstorm)
- Comprehensive aspects-map.md with TYPE metadata and dependencies
- One command creates entire planning architecture
- Interactive gates maintain this philosophy while adding validation checkpoints

**Enhanced Intelligence:**
- Extensive sequential thinking for aspect TYPE categorization
- Dependency graph analysis for optimal ordering
- Conditional aspect auto-detection (Security, AI/ML, Migration)
- Consideration of VibeWiz workflow downstream needs
- Aspect metadata feeds into workflow commands (DRD, tools, ux-map, etc.)

**Collaborative Structure Creation:**
- Interactive gates replace automated monologue with dialogue
- Up to 3 iterations per gate for refinement
- User sees full scope immediately with TYPE classifications
- Clear brainstorming roadmap with dependency rationale
- No structural surprises during planning

## Command Structure

```bash
/aspects [project-name]

# Examples:
/aspects nutri
/aspects culinary-quest
/aspects ai-assistant
```

**Note:** This command ONLY runs at project root level after `/explore`.

## Process Overview

```
1. Parse & Validate → Read project-core.md
2. Extract Complete Scope → Understand all planning domains
3. GATE 1: Main Aspects Identification (interactive approval)
4. GATE 2: Complete Tree Structure (interactive approval)
5. GATE 3: Final Review & Brainstorm Plan (interactive approval)
6. Generate folder structure + aspects-map.md
```

**🚨 CRITICAL REMINDERS BEFORE STARTING:**
1. **DO NOT** create ANY brainstorm-structure.md files - /brainstorm handles ALL of those
2. **DO NOT** worry about scope size - embrace the FULL project scope (5 aspects or 500)
3. **DO NOT** limit depth - go as deep as needed (2 levels or 6+ levels)
4. **DO NOT** make implementation decisions - NO specific APIs, libraries, services, or technical approaches
5. **DO NOT** include time estimates - can't estimate before brainstorming
6. **DO ONLY**: Create empty folders + aspects-map.md with TYPE metadata and QUESTIONS
7. **PURPOSE**: Define WHAT to explore, not HOW to build it - complete structural analysis for one-shot vibecoding

**WHAT TO AVOID IN ASPECT DESCRIPTIONS:**
- ❌ Specific API names (Stripe, OpenAI, Binance, etc.)
- ❌ Specific libraries/frameworks (React, WebSocket, etc.)
- ❌ Implementation details (schema structures, algorithm choices)
- ❌ Time/session estimates
- ❌ "How to build" statements

**WHAT TO INCLUDE IN ASPECT DESCRIPTIONS:**
- ✅ Problem domain definition
- ✅ Questions to explore
- ✅ Concerns to address
- ✅ Integration points with other aspects
- ✅ TYPE classification

---

## Step 1: Parse and Validate

- Extract project name from arguments
- Verify project exists at `/Projects/[project-name]/`
- Confirm `exploration-initial.md` exists
- Verify this is project root analysis (not sub-aspect)

---

## Step 2: Read Input Documents

**Primary Input - project-core.md (if exists):**
Read `.wiz/project-core.md` first:
- This is the authoritative source for project scope
- Contains finalized feature list, user personas, technical scope
- If this file exists, use it as primary input

**Fallback Input - exploration-initial.md:**
If project-core.md doesn't exist:
- Read `.wiz/exploration/exploration-initial.md`
- Warn user: "⚠️ Project core not yet defined. Recommend running /core first for better-informed aspect structure. Proceeding with exploration-initial.md only."
- Identify all major planning areas
- Detect multi-layered complexity requiring nested breakdown
- Understand scope breadth and depth

---

## Step 3: EXTENSIVE Ultra-Think Main Aspects Identification

Use `mcp__sequential-thinking__sequentialthinking` EXTENSIVELY (15-30+ thinks) to:

**Identify Aspect TYPES (Critical for Workflow):**

Master Claude shall categorize aspects by TYPE to feed downstream workflow commands:

1. **Data Aspects** 🗄️
   - Database schema design
   - Entity relationships
   - Data validation rules
   - Migration strategies
   - **Feeds into:** /drd (Data Requirements Document)

2. **Foundational/Technical Aspects** 🏗️
   - Core architecture decisions
   - Authentication/authorization
   - Security patterns
   - Performance requirements
   - Infrastructure needs
   - **Feeds into:** /tools (stack selection), architecture.md

3. **Feature Aspects** ⚡
   - User-facing functionality
   - Business logic
   - User workflows
   - **Feeds into:** PRD-master, PRD-phase, /summary

4. **Integration Aspects** 🔌
   - Third-party APIs
   - External services
   - Webhooks/events
   - **Feeds into:** /tools, architecture.md

5. **UX/Design Aspects** 🎨
   - Visual identity (colors, typography, brand aesthetics)
   - User flows (navigation, journeys, state management)
   - Component patterns (reusable components, design system)
   - Layout architecture (grid system, responsive strategy, whitespace)
   - Accessibility (WCAG compliance, keyboard nav, screen readers)
   - **Feeds into:** /ux-map, /ui-layout, /ui-design, /blueprint
   - **CRITICAL:** Auto-create comprehensive UX aspect tree for all user-facing projects

6. **Content Aspects** 📄
   - Content types
   - Content sources
   - Media management
   - CMS requirements
   - Localization
   - **Feeds into:** /content (content sourcing & catalog)

7. **Deployment/Infrastructure Aspects** 🚀
   - CI/CD pipelines
   - Monitoring
   - Logging
   - Scaling strategies
   - **Feeds into:** /tools, deployment strategy

8. **Enhancement Aspects** ✨
   - Advanced features
   - Optimizations
   - Analytics
   - Nice-to-have features
   - **Feeds into:** Later phases in /phases

9. **Security & Compliance Aspects** 🔒 *(CONDITIONAL - only if detected)*
   - Authentication/Authorization mechanisms
   - Data protection & encryption
   - Compliance requirements (GDPR, HIPAA, PCI-DSS, etc.)
   - API security & rate limiting
   - Input validation & sanitization
   - Session management
   - Audit logging
   - **Feeds into:** /tools, architecture.md, PRD security requirements
   - **CRITICAL:** Auto-detect need based on exploration content

10. **AI/ML Aspects** 🤖 *(CONDITIONAL - only if detected)*
   - LLM integrations (GPT, Claude, local models)
   - Machine learning models (training, inference, versioning)
   - Prompt engineering & management
   - Vector databases & embeddings
   - AI-generated content systems
   - Model monitoring & cost optimization
   - Context management & RAG
   - **Feeds into:** /tools (model selection), architecture.md (AI patterns), PRD (AI features)
   - **CRITICAL:** Auto-detect need based on exploration content

11. **Migration/Legacy Aspects** 🔄 *(CONDITIONAL - BROWNFIELD ONLY)*
   - Data migration strategies (ETL, transformation, validation)
   - Feature parity analysis (port vs deprecate)
   - Phased rollout strategies (pilot, gradual, big-bang)
   - Backward compatibility during transition
   - Cutover & rollback plans
   - Legacy system integration patterns
   - **Feeds into:** /phases (migration phases), /tools (migration tools), architecture.md
   - **CRITICAL:** Auto-detect ONLY for brownfield/replacement projects

## Conditional Aspect Auto-Detection

**3 Special Types - Add ONLY if triggers detected during ultra-thinking:**

### 🔒 Security & Compliance (LAYER 1 if detected)

**Triggers:** User accounts, sensitive data (PII/PHI/financial), payments, APIs, multi-tenant, admin functions, compliance mentioned (GDPR/HIPAA/PCI)

**Context-aware detection:**
- ✅ "user accounts" / "user login" / "authentication" → Security needed
- ❌ "user interface" / "user experience" → Just UX terminology, no security

**Sub-aspects:** authentication-authorization, data-protection, compliance-requirements, api-security, audit-monitoring

**Skip if:** Static site, read-only content, no data persistence, no accounts

---

### 🤖 AI/ML (LAYER 1 if core, LAYER 2 if supporting)

**Triggers:** LLM integrations (GPT/Claude/local models), ML models, AI-generated content, vector databases, semantic search, embeddings, prompt engineering

**Layer placement:**
- LAYER 1 if AI/ML is core product (AI writing tool, recommendation engine)
- LAYER 2 if AI/ML supports features (smart search in e-commerce app)

**Sub-aspects:** model-architecture, prompt-engineering, context-management, quality-monitoring, cost-optimization

**Skip if:** Traditional application without AI features

---

### 🔄 Migration/Legacy (LAYER 1 - BROWNFIELD ONLY)

**Triggers:** Replacing existing system, data migration needed, feature parity requirements, legacy integration, existing users transitioning

**CRITICAL:** ONLY for brownfield (replacing existing system). Skip entirely for greenfield (new projects).

**Detection questions:**
- Is there an existing system being replaced? → Yes = Add migration aspects
- Is there existing data to preserve? → Yes = Data migration sub-aspect
- Are users currently using old system? → Yes = User migration planning

**Sub-aspects:** data-migration (ETL/transformation), feature-parity-analysis, phased-rollout, legacy-integration, cutover-plans

**Skip if:** Greenfield (new build), no predecessor, fresh startup, proof-of-concept

---

**Detection Methodology:**

During EXTENSIVE ultra-thinking (Step 3), explicitly ask:
1. "Does this project need Security & Compliance?" → Check triggers above
2. "Does this project use AI/ML?" → Check triggers above, determine layer
3. "Is this brownfield or greenfield?" → Brownfield only = add Migration aspects

**Identify Aspect COLLABORATION-TYPE (User Involvement Classification - NEW):**

Master Claude shall ALSO categorize aspects by COLLABORATION-TYPE (orthogonal to TYPE above).

**Purpose:** Separate user-dependent aspects (creative/strategic) from Claude-autonomous aspects (research/technical) to enable user-first workflow.

**COLLABORATION-TYPE Categories:**

📝 **USER-CREATIVE**
- Requires human vision, imagination, branding, authenticity
- Cannot be researched - needs founder's/user's unique voice and ideas
- Examples: Product differentiation, naming, brand identity, UX philosophy, unique value propositions
- Dialogue approach: Open-ended exploration, capture user's authentic vision
- **Keywords:** "unique," "differentiation," "brand," "philosophy," "voice," "personality," "what makes this special"

🎯 **USER-STRATEGIC**
- Requires business decisions, prioritization, risk tolerance
- Claude can inform with data/analysis, but user must decide
- Examples: Pricing tiers, target market priority, feature vs cost tradeoffs, go-to-market strategy
- Dialogue approach: Present options with tradeoff analysis, facilitate decision-making
- **Keywords:** "pricing," "priority," "tradeoff," "target market," "business model," "risk tolerance"

🤝 **USER-INFORMED**
- Technical/architectural decisions informed by user's strategic choices from Phase 1
- Claude researches options, user confirms based on constraints from strategic aspects
- Examples: Database choice (after scale requirements known), authentication method (after security requirements known)
- Dialogue approach: Research + present recommendations with rationale, get confirmation
- **Keywords:** "architecture for [user requirement]," "how to achieve [user goal]," "technical approach to [user need]"

⚡ **CLAUDE-AUTONOMOUS**
- Research/technical decisions with objective best practices
- User involvement: Review recommendation, rubber-stamp or raise specific concerns
- Examples: Timezone handling (always UTC), compression codecs, indexing strategies, caching patterns
- Dialogue approach: Research → recommend → minimal dialogue, just confirmation
- **Keywords:** "standard," "best practice," "optimal," "proven pattern," "industry standard"

**COLLABORATION-TYPE vs TYPE (Two Dimensions):**

TYPE = **What workflow commands need this** (Data → /drd, Feature → PRD, UX → /ux-map)
COLLABORATION = **How much user involvement needed** (Creative → deep dialogue, Autonomous → quick confirm)

**Example: compound-database aspect could be:**
- TYPE: Data (feeds /drd) ← workflow classification
- COLLABORATION: USER-CREATIVE (compound selection requires product vision) ← user involvement

**For EACH Main Aspect:**

- **Determine TYPE**: What category does this aspect belong to? (Data/Foundational/Feature/etc.)
- **Determine COLLABORATION-TYPE**: How much user involvement needed? (USER-CREATIVE/USER-STRATEGIC/USER-INFORMED/CLAUDE-AUTONOMOUS)
- **Identify Sub-Aspects**: Does this need breakdown into focused areas? Create as many as needed!
- **Determine Depth**: Do any sub-aspects need sub-sub-aspects? Sub-sub-sub-aspects? Continue recursively!
- **Continue recursively to ANY depth** until reaching focused "leaves" - could be 2 levels, could be 5+ levels
- **NO LIMITS** on breadth or depth - represent the FULL scope needed for complete planning

**Example TYPE Analysis for Nutri:**
```
Data Aspects:
├── compound-database (Data + Feature hybrid)
│   └── Feeds: /drd, PRD-master
└── nutritional-tracking (Data + Feature hybrid)
    └── Feeds: /drd, PRD-master

Foundational/Technical:
├── authentication-architecture (Foundational)
│   └── Feeds: /tools, architecture.md
└── real-time-sync-engine (Technical)
    └── Feeds: /tools, architecture.md

Security/Compliance: 🔒 *(detected: user accounts + sensitive health data)*
└── security-and-compliance (Security)
    ├── Authentication/Authorization (user accounts detected)
    ├── Data Protection (health data = sensitive PII)
    └── Compliance Requirements (GDPR for EU users, potential HIPAA if health advice)
    └── Feeds: /tools, architecture.md, PRD security requirements

AI/ML: 🤖 *(detected IF: personalized meal recommendations, nutrition analysis)*
└── ai-ml (AI/ML) [LAYER 2 - supporting feature]
    ├── Model Architecture (recommendation engine, nutrition NLP)
    ├── AI Feature Design (where AI personalizes experience)
    └── Monitoring/Evaluation (recommendation quality, user satisfaction)
    └── Feeds: /tools, architecture.md, PRD AI features
    └── NOTE: Only include if project explicitly mentions AI/ML features

Migration/Legacy: 🔄 *(NOT DETECTED - greenfield project, no legacy system)*
└── NO migration aspects (building from scratch)

UX/Design:
├── design-system (UX/Design)
│   └── Feeds: /ux-map, /ui, /blueprint
└── accessibility-framework (UX/Design)
    └── Feeds: /ux-map, /ui

Feature Aspects:
├── food-filtering (Feature)
│   └── Feeds: PRD-master, /summary
└── meal-planning (Feature)
    └── Feeds: PRD-master, /summary

Content Aspects:
├── food-database-sourcing (Content)
│   └── Feeds: /content
└── recipe-integration (Content + Feature hybrid)
    └── Feeds: /content, PRD-master
```

**Determine Dependencies:**
- Which aspects must be brainstormed before others?
- What dependencies exist between aspects?
- What's the optimal brainstorming order?
- Which aspects are blocking dependencies (CRITICAL)?

**Prioritize by Dependency Layers:**

```
LAYER 1: FOUNDATION (CRITICAL - No Dependencies) 🧙‍♂️
├── Data schema aspects (blocks all features)
├── Authentication architecture (blocks user features)
├── Security & Compliance (blocks secure features - if detected) 🔒
├── Migration/Legacy (blocks all work until migration strategy set - if brownfield) 🔄
├── Core technical architecture (blocks all implementation)
└── Design system foundations (blocks UX work)

LAYER 1-2: CONDITIONAL FOUNDATION/INFRASTRUCTURE 🤖
└── AI/ML aspects (LAYER 1 if core product, LAYER 2 if supporting - if detected)

LAYER 2: INFRASTRUCTURE (Depends on Foundation) 🏗️
├── Database setup (depends on schema)
├── API architecture (depends on auth + schema)
├── State management (depends on architecture)
└── Content management system (depends on schema + architecture)

LAYER 3: FEATURES (Depends on Infrastructure) ⚡
├── Core user features (depends on API + data)
├── Admin features (depends on auth + features)
└── Integration features (depends on API architecture)

LAYER 4: ENHANCEMENTS (Depends on Features) ✨
├── Performance optimization (depends on features)
├── Advanced UX patterns (depends on features)
└── Analytics/monitoring (depends on features)
```

**Consider VibeWiz Workflow Needs:**

Think about how aspects feed into downstream commands:
- PRD generation needs: Feature aspects, user journey aspects
- DRD generation needs: Data aspects, schema aspects
- /tools needs: Technical infrastructure aspects, integration aspects
- /content needs: Content strategy aspects, content source aspects
- /ux-map needs: Design system, UX flow aspects, all feature aspects
- /ui needs: Design system, visual design aspects
- /blueprint needs: Component architecture aspects

This TYPE metadata ensures comprehensive coverage for the ENTIRE VibeWiz workflow!

---

## Step 4: GATE 1 - Main Aspects Identification

### 4A. Present Main Aspects to User

**STOP and present findings before proceeding to sub-aspect breakdown.**

Format the presentation exactly as shown:

```markdown
## GATE 1: Main Aspects Identification

Master Claude has identified X main aspects from project-core.md:

### LAYER 1: FOUNDATION (CRITICAL) 🧙‍♂️
1. **[aspect-name]** [Type: Data/Foundational/etc.] [Collab: USER-CREATIVE/etc.]
   - Problem Domain: [1-2 sentence description of WHAT to explore]
   - Blocks: [which aspects/features depend on this]
   - Feeds: [which workflow commands need this]

2. **[aspect-name]** [Type: X] [Collab: Y]
   - Problem Domain: [...]
   - Blocks: [...]
   - Feeds: [...]

[... continue for all LAYER 1 aspects ...]

### LAYER 2: INFRASTRUCTURE (HIGH) 🏗️
[... aspects that depend on Layer 1 ...]

### LAYER 3: FEATURES (MEDIUM-HIGH) ⚡
[... aspects that depend on Layer 2 ...]

### LAYER 4: ENHANCEMENTS (MEDIUM-LOW) ✨
[... final layer aspects ...]

---

### Conditional Aspects Detection Summary:

**Security & Compliance** 🔒
[If detected] ✅ AUTO-DETECTED based on:
- [List specific triggers: user accounts, sensitive data (PII/health/financial), payments, API security, multi-tenant, compliance requirements]
- Layer Placement: LAYER 1 (blocks secure features)
[If not detected] ❌ No security aspects needed - [reason: static site/read-only/no auth/no sensitive data]

**AI/ML** 🤖
[If detected] ✅ AUTO-DETECTED based on:
- [List specific triggers: LLM integrations, ML models, AI-generated content, vector databases, semantic search, recommendations]
- Layer Placement: [LAYER 1 if core product / LAYER 2 if supporting feature]
[If not detected] ❌ No AI/ML aspects needed - traditional application

**Migration/Legacy** 🔄
[If detected] ✅ AUTO-DETECTED - BROWNFIELD PROJECT:
- Migrating from: [legacy system name]
- Triggers: [data migration, feature parity, existing users, legacy integration]
- Layer Placement: LAYER 1 (blocks all work until migration strategy set)
[If not detected] ❌ GREENFIELD PROJECT - no migration aspects needed

---

**Total Main Aspects:** X
**Dependency Layers:** Y layers deep

Do these main aspects cover the complete scope, initiate Klyve Dahl?

**Response options:**
- "approved" → Move to Gate 2 (sub-aspect breakdown)
- "change: [description]" → Adjust and present again (up to 3 iterations)
```

### 4B. Wait for User Response

**CRITICAL:** Stop execution and wait for user input. Do NOT proceed until user responds.

### 4C. Parse User Response & Iteration Logic

**If user responds "approved":**
- Proceed to Step 5 (sub-aspect breakdown)

**If user responds "change: [description]":**
- Parse the change request
- Track iteration count (max 3 iterations for Gate 1)
- If iteration count > 3:
  - Inform user: "Master Claude has reached maximum iterations (3) for Gate 1. Proceeding with current aspect structure."
  - Proceed to Step 5
- Otherwise:
  - Apply requested changes using sequential thinking
  - Re-present Gate 1 with adjustments
  - Increment iteration counter
  - Wait for response again

**If user response is unclear:**
- Ask for clarification: "Master Claude needs clarification, initiate. Please respond with 'approved' or 'change: [specific description of what to adjust]'."

---

## Step 5: EXTENSIVE Ultra-Think Sub-Aspect Breakdown

**ONLY reach this step if Gate 1 is approved.**

Use `mcp__sequential-thinking__sequentialthinking` EXTENSIVELY (15-30+ thinks) to:

**For EACH Main Aspect (approved in Gate 1):**

- **Identify Sub-Aspects**: Does this need breakdown into focused areas? Create as many as needed!
- **Determine Depth**: Do any sub-aspects need sub-sub-aspects? Sub-sub-sub-aspects? Continue recursively!
- **Continue recursively to ANY depth** until reaching focused "leaves" - could be 2 levels, could be 5+ levels
- **NO LIMITS** on breadth or depth - represent the FULL scope needed for complete planning
- **Assign TYPEs to sub-aspects**: Each sub-aspect gets TYPE classification
- **Validate completeness**: Does this sub-aspect tree cover everything needed for the main aspect?

**Determine Brainstorming Sequence:**
- Assign sequential numbers (1, 2, 3, ...) based on dependency order
- LAYER 1 aspects get 1, 2, 3..., then LAYER 2 continues numbering, then LAYER 3, etc.
- Sequential across ALL layers (not restarting per layer)
- These numbers become folder prefixes (1-, 2-, 1.1-, 1.2-, etc.)

**Folder Name Preparation:**
- Sanitize all aspect names for filesystem compatibility
- Convert to lowercase kebab-case (hyphens between words)
- Remove ALL special characters: `{ } [ ] ( ) < > " ' / \ | ? * : ;`
- Replace spaces with hyphens
- Remove multiple consecutive hyphens

**Examples:**
- `Design System` → `1-design-system`
- `User Authentication & Sessions` → `2-user-authentication-sessions`
- `Visual Identity` (under Design System) → `1.1-visual-identity`
- `Real-Time (WebSocket) Sync` → `3-real-time-websocket-sync`

---

## Step 6: GATE 2 - Complete Tree Structure

### 6A. Present Complete Tree to User

**STOP and present complete tree structure before generating folders.**

Format the presentation exactly as shown:

```markdown
## GATE 2: Complete Tree Structure

Master Claude has expanded all main aspects into complete sub-aspect trees:

### LAYER 1: FOUNDATION (CRITICAL) 🧙‍♂️

├── **1-[aspect-name]** [Type: Data] [Collab: USER-CREATIVE] [6 sub-aspects]
│   ├── 1.1-[sub-name] [Type: Data]
│   ├── 1.2-[sub-name] [Type: Data] [3 sub-sub-aspects]
│   │   ├── 1.2.1-[sub-sub-name]
│   │   ├── 1.2.2-[sub-sub-name]
│   │   └── 1.2.3-[sub-sub-name]
│   ├── 1.3-[sub-name] [Type: Feature]
│   ├── 1.4-[sub-name] [Type: Data]
│   ├── 1.5-[sub-name] [Type: Feature]
│   └── 1.6-[sub-name] [Type: Feature]
│
├── **2-[aspect-name]** [Type: Security] [5 sub-aspects] 🔒
│   ├── 2.1-[sub-name]
│   ├── 2.2-[sub-name]
│   ├── 2.3-[sub-name]
│   ├── 2.4-[sub-name]
│   └── 2.5-[sub-name]
│
[... continue for all aspects in all layers ...]

---

### Brainstorming Sequence (Dependency-Ordered):

**LAYER 1 - Foundation (CRITICAL):**
1. [ ] 1-[aspect-name] (0/6 sub-aspects) → Blocks: all features
2. [ ] 2-[aspect-name] (0/5 sub-aspects) → Blocks: auth, API
3. [ ] 3-[aspect-name] (0/8 sub-aspects) → Blocks: UI work

**LAYER 2 - Infrastructure (HIGH):**
4. [ ] 4-[aspect-name] (0/3 sub-aspects) → Depends: 1-[aspect]
5. [ ] 5-[aspect-name] (0/5 sub-aspects) → Depends: 1-[aspect], 2-[aspect]

[... continue for all layers ...]

---

**Statistics:**
- **Main Aspects:** X
- **Total Sub-Aspects:** Y (all depths)
- **Total Aspects:** Z
- **Maximum Depth:** N levels

**Type Distribution:**
- Data: X aspects 🗄️
- Foundational: Y aspects 🏗️
- Feature: Z aspects ⚡
- Security: N aspects 🔒
[... etc ...]

Does this tree structure have appropriate depth and coverage, initiate Klyve Dahl?

**Response options:**
- "approved" → Move to Gate 3 (final review)
- "change: [description]" → Adjust tree and present again (up to 3 iterations)
```

### 6B. Wait for User Response

**CRITICAL:** Stop execution and wait for user input. Do NOT proceed until user responds.

### 6C. Parse User Response & Iteration Logic

**If user responds "approved":**
- Proceed to Step 7 (generate aspects-map preview)

**If user responds "change: [description]":**
- Parse the change request
- Track iteration count (max 3 iterations for Gate 2)
- If iteration count > 3:
  - Inform user: "Master Claude has reached maximum iterations (3) for Gate 2. Proceeding with current tree structure."
  - Proceed to Step 7
- Otherwise:
  - Apply requested changes using sequential thinking
  - Re-present Gate 2 with adjustments
  - Increment iteration counter
  - Wait for response again

**If user response is unclear:**
- Ask for clarification: "Master Claude needs clarification, initiate. Please respond with 'approved' or 'change: [specific description of what to adjust]'."

---

## Step 7: Generate aspects-map.md Preview

**ONLY reach this step if Gate 2 is approved.**

Generate a complete aspects-map.md document preview (don't write to file yet) with all sections populated. This preview will be shown in Gate 3.

---

## Step 8: GATE 3 - Final Review & Brainstorm Plan

### 8A. Present Complete Plan to User

**STOP and present final review before creating any folders or files.**

Format the presentation exactly as shown:

```markdown
## GATE 3: Final Review & Brainstorm Plan

### Summary Statistics
- **Main Aspects:** X
- **Total Sub-Aspects:** Y (all depths)
- **Total Aspects:** Z
- **Maximum Depth:** N levels
- **Conditional Aspects Detected:** [Security 🔒, AI/ML 🤖, Migration 🔄, or "None"]

### Type Distribution
- Data: X aspects 🗄️
- Foundational: Y aspects 🏗️
- Feature: Z aspects ⚡
- Integration: N aspects 🔌
- UX/Design: N aspects 🎨
- Content: N aspects 📄
- Deployment: N aspects 🚀
- Security: N aspects 🔒 *(if detected)*
- AI/ML: N aspects 🤖 *(if detected)*
- Migration: N aspects 🔄 *(if brownfield)*
- Enhancement: N aspects ✨

### Collaboration Distribution
- USER-CREATIVE: X aspects 📝 (deep dialogue needed)
- USER-STRATEGIC: Y aspects 🎯 (user must decide)
- USER-INFORMED: Z aspects 🤝 (research + confirmation)
- CLAUDE-AUTONOMOUS: N aspects ⚡ (minimal dialogue)

### Folder Structure Preview
```
.wiz/exploration/aspects/
├── 1-[main-aspect-1]/
│   └── aspects/
│       ├── 1.1-[sub]/
│       ├── 1.2-[sub]/
│       │   └── aspects/
│       │       ├── 1.2.1-[sub-sub]/
│       │       └── 1.2.2-[sub-sub]/
│       └── 1.3-[sub]/
├── 2-[main-aspect-2]/
│   └── aspects/
│       └── ... (all sub-aspects with 2.N- numbering)
[... complete structure ...]
```

### Workflow Command Mapping

**Which aspects feed into which VibeWiz workflow commands:**
- **/drd** (Data Requirements) → [list Data-type aspects]
- **/tools** (Stack Selection) → [list Foundational/Integration/Security/AI aspects]
- **/content** (Content Strategy) → [list Content aspects]
- **/ux-map** (UX Architecture) → [list UX/Feature aspects]
- **/ui** (Visual Templates) → [list UX/Design aspects]
- **/blueprint** (Component Architecture) → [list UX aspects]
- **PRD-master** → [list Feature/Enhancement aspects]
- **/phases** → ALL aspects (uses complete SUMMARY tree)

### Next Steps After Generation

1. **Folder creation**: Master Claude will create Z empty folders with sequential numbering
2. **aspects-map.md**: Complete navigation and reference document
3. **Begin brainstorming**: `/brainstorm [project]` (auto-navigates tree)
4. **Evaluation**: `/evaluate-aspect` after each main aspect complete
5. **Summarization**: `/summarize-aspect` after evaluation approval
6. **Repeat** until all aspects explored
7. **Proceed to**: /phases, /drd, /tools, /content, /ux-map, etc.

---

Ready to generate complete aspect structure, initiate Klyve Dahl?

**Response options:**
- "approved" → Generate folders + aspects-map.md
- "change: [description]" → Final adjustments (up to 3 iterations)
```

### 8B. Wait for User Response

**CRITICAL:** Stop execution and wait for user input. Do NOT proceed until user responds.

### 8C. Parse User Response & Iteration Logic

**If user responds "approved":**
- Proceed to Step 9 (create folder structure)

**If user responds "change: [description]":**
- Parse the change request
- Track iteration count (max 3 iterations for Gate 3)
- If iteration count > 3:
  - Inform user: "Master Claude has reached maximum iterations (3) for Gate 3. Proceeding with current plan."
  - Proceed to Step 9
- Otherwise:
  - Apply requested changes
  - Regenerate aspects-map preview if needed
  - Re-present Gate 3 with adjustments
  - Increment iteration counter
  - Wait for response again

**If user response is unclear:**
- Ask for clarification: "Master Claude needs clarification, initiate. Please respond with 'approved' or 'change: [specific description of what to adjust]'."

---

## Step 9: Create Complete Folder Structure

**ONLY reach this step if all 3 gates are approved.**

**🔢 FOLDER NAMING CONVENTIONS (CRITICAL):**

All aspect folders MUST follow sequential numbering based on brainstorming order from aspects-map.md:

**Main Aspect Numbering:**
- Prefix with sequence number from BRAINSTORMING SEQUENCE order
- Format: `[N]-[folder-name]`
- Examples: `1-design-system`, `2-platform-data-model`, `3-security-compliance`

**Sub-Aspect Numbering (Recursive):**
- Prefix with parent number + sub-sequence
- Format: `[N.M]-[folder-name]` → `[N.M.P]-[folder-name]` → etc.
- Examples:
  - Under `1-design-system/aspects/`: `1.1-visual-identity`, `1.2-layout-architecture`
  - Under `1.1-visual-identity/aspects/`: `1.1.1-typography`, `1.1.2-color-palette`
  - Under `2-platform-data-model/aspects/`: `2.1-user-accounts`, `2.2-farm-profiles`

**Folder Name Sanitization (CRITICAL):**
- Convert to lowercase kebab-case (hyphens between words)
- Remove ALL special characters: `{ } [ ] ( ) < > " ' / \ | ? * : ;`
- Replace spaces with hyphens
- Remove multiple consecutive hyphens
- Examples:
  - `Design System` → `design-system`
  - `User Authentication & Sessions` → `user-authentication-sessions`
  - `Real-Time (WebSocket) Sync` → `real-time-websocket-sync`
  - `API {External} Integration` → `api-external-integration`

**Generate ENTIRE tree with numbered folders:**

```
.wiz/exploration/
├── exploration-initial.md (existing)
├── aspects-map.md (NEW - complete planning map with TYPE metadata)
└── aspects/
    ├── 1-[main-aspect-1]/          (numbered - empty except future brainstorm files)
    │   └── aspects/
    │       ├── 1.1-[sub-aspect-1]/     (numbered - empty folder)
    │       ├── 1.2-[sub-aspect-2]/     (numbered - empty folder)
    │       │   └── aspects/
    │       │       ├── 1.2.1-[sub-sub-1]/ (numbered - empty folder)
    │       │       └── 1.2.2-[sub-sub-2]/ (numbered - empty folder)
    │       └── 1.3-[sub-aspect-3]/     (numbered - empty folder)
    ├── 2-[main-aspect-2]/          (numbered - empty except future brainstorm files)
    │   └── aspects/
    │       └── ... (all sub-aspects with 2.N- numbering)
    └── ... (all main aspects with sequential numbering)
```

**Numbering Source:**
- Main aspect numbers: Use order from "📋 BRAINSTORMING SEQUENCE (Dependency-Ordered)" section in aspects-map.md
- LAYER 1 aspects get 1, 2, 3..., then LAYER 2 continues numbering, then LAYER 3, etc.
- Sequential across ALL layers (not restarting per layer)

**Key Points:**
- ALL aspects get empty folders with sequential numbering
- Numbering reflects brainstorming order (dependency-aware)
- NO brainstorm-structure.md files created (moved to /brainstorm command)
- Structure created to full depth discovered in ultra-thinking
- Folders ready to receive brainstorm files from /brainstorm command
- Folder names sanitized (no special characters, kebab-case)

---

## Step 10: Generate Final aspects-map.md

Create optimized `aspects-map.md` with **navigation info at top**, **detailed descriptions below**:

```markdown
# [Project Name] - Aspects Map & Navigation

*Optimized for /brainstorm navigation: Quick Reference at top, detailed descriptions below.*

---
## 📍 QUICK REFERENCE (Read this section for navigation)
---

### Aspect Completion TODO

**Purpose:** Instant position detection for /brainstorm command. Generate this dynamically based on discovered aspects in dependency order.

**Format:**
```
- [ ] 1-[aspect-name] (0/N subs) | Layer X | [Type]
- [ ] 2-[aspect-name] (0/N subs) | Layer X | [Type]
- [ ] 3-[aspect-name] (0/N subs) | Layer X | [Type]
...
```

**Status Markers:**
- `[ ]` = Not started (pending)
- `[~]` = In progress (current aspect - brainstorm-structure.md exists)
- `[x]` = Complete (SUMMARY.md exists)

**Example:**
```
- [ ] 1-compound-database (0/5 subs) | Layer 1 | Data
- [ ] 2-security-compliance (0/5 subs) | Layer 1 | Security
- [ ] 3-data-architecture (0/4 subs) | Layer 1 | Foundational
- [ ] 4-design-system (0/6 subs) | Layer 1 | UX
- [ ] 5-multi-source-integration (0/7 subs) | Layer 2 | Integration
- [ ] 6-ai-ml-integration (0/5 subs) | Layer 2 | AI/ML
...
```

**Usage:**
- /brainstorm reads this TODO (lines 1-100) to instantly find current position
- Finds first `[~]` (in progress) or `[ ]` (pending) aspect
- <3 second position detection vs 15-20 seconds with old search logic

---

### Overview Stats
- **Main-Tier Aspects:** [N]
- **Total Sub-Aspects:** [N]
- **Sub-Sub-Aspects:** [N]
- **Maximum Depth:** [N] levels
- **Total Aspects to Explore:** [N]
- **Conditional Aspects Detected:** [List: Security 🔒, AI/ML 🤖, Migration 🔄 if applicable, or "None"]

**Note:** No time/session estimates - brainstorming determines actual effort.

### Aspect Type Distribution
- **Data:** [N] aspects 🗄️
- **Foundational/Technical:** [N] aspects 🏗️
- **Feature:** [N] aspects ⚡
- **Integration:** [N] aspects 🔌
- **UX/Design:** [N] aspects 🎨
- **Content:** [N] aspects 📄
- **Deployment:** [N] aspects 🚀
- **Security/Compliance:** [N] aspects 🔒 *(if detected)*
- **AI/ML:** [N] aspects 🤖 *(if detected)*
- **Migration/Legacy:** [N] aspects 🔄 *(if brownfield)*
- **Enhancement:** [N] aspects ✨

### Collaboration Type Distribution (NEW - User Involvement Classification)
- **USER-CREATIVE:** [N] aspects 📝 (vision/branding - deep dialogue needed)
- **USER-STRATEGIC:** [N] aspects 🎯 (business decisions - user must decide)
- **USER-INFORMED:** [N] aspects 🤝 (technical informed by user constraints)
- **CLAUDE-AUTONOMOUS:** [N] aspects ⚡ (research/best practices - minimal dialogue)

---

### 🗺️ COMPLETE TREE (Compact View - Navigation Only)

**Status Legend:** [ ] Not started | [~] In progress | [✓] Complete

**NOTE:** Folder names include sequential numbering (1-, 2-, 1.1-, 1.2-, etc.) for organized navigation.

```
LAYER 1: FOUNDATION (CRITICAL) 🧙‍♂️
├── [ ] 1-main-aspect-1/ [Type: Data] [L1] [0/6 sub-aspects]
│   ├── [ ] 1.1-sub-aspect-1-1/ [Type: Data] [0/2 sub-sub]
│   ├── [ ] 1.2-sub-aspect-1-2/ [Type: Data] [0/0 sub-sub]
│   ├── [ ] 1.3-sub-aspect-1-3/ [Type: Data] [0/3 sub-sub]
│   │   ├── [ ] 1.3.1-sub-sub-1-3-1/
│   │   ├── [ ] 1.3.2-sub-sub-1-3-2/
│   │   └── [ ] 1.3.3-sub-sub-1-3-3/
│   ├── [ ] 1.4-sub-aspect-1-4/ [Type: Feature] [0/0 sub-sub]
│   ├── [ ] 1.5-sub-aspect-1-5/ [Type: Data] [0/0 sub-sub]
│   └── [ ] 1.6-sub-aspect-1-6/ [Type: Feature] [0/0 sub-sub]
├── [ ] 2-main-aspect-2/ [Type: Foundational] [L1] [0/4 sub-aspects]
│   ├── [ ] 2.1-sub-aspect-2-1/ [Type: Foundational] [0/0 sub-sub]
│   ├── [ ] 2.2-sub-aspect-2-2/ [Type: Foundational] [0/0 sub-sub]
│   ├── [ ] 2.3-sub-aspect-2-3/ [Type: Technical] [0/0 sub-sub]
│   └── [ ] 2.4-sub-aspect-2-4/ [Type: Foundational] [0/0 sub-sub]
├── [ ] 3-security-compliance/ [Type: Security] [L1] [0/5 sub-aspects] *(if detected)*
│   └── [... sub-aspects with 3.N- numbering ...]
└── [ ] 4-design-system/ [Type: UX] [L1] [0/8 sub-aspects]
    └── [... sub-aspects with 4.N- numbering ...]

LAYER 2: INFRASTRUCTURE (HIGH) 🏗️
├── [ ] 5-main-aspect-3/ [Type: Technical] [L2] [0/3 sub-aspects]
│   └── [... sub-aspects with 5.N- numbering ...]
├── [ ] 6-main-aspect-4/ [Type: Integration] [L2] [0/5 sub-aspects]
│   └── [... sub-aspects with 6.N- numbering ...]
└── [ ] 7-ai-ml/ [Type: AI/ML] [L2] [0/5 sub-aspects] *(if supporting feature)*
    └── [... sub-aspects with 7.N- numbering ...]

LAYER 3: FEATURES (MEDIUM-HIGH) ⚡
├── [ ] 8-main-aspect-5/ [Type: Feature] [L3] [0/4 sub-aspects]
│   └── [... sub-aspects with 8.N- numbering ...]
└── [ ] 9-main-aspect-6/ [Type: Feature] [L3] [0/6 sub-aspects]
    └── [... sub-aspects with 9.N- numbering ...]

LAYER 4: ENHANCEMENTS (MEDIUM-LOW) ✨
├── [ ] 10-main-aspect-7/ [Type: Enhancement] [L4] [0/3 sub-aspects]
│   └── [... sub-aspects with 10.N- numbering ...]
└── [ ] 11-main-aspect-8/ [Type: Enhancement] [L4] [0/2 sub-aspects]
    └── [... sub-aspects with 11.N- numbering ...]
```

---

### 📋 BRAINSTORMING SEQUENCE (Dependency-Ordered with Progress)

**NOTE:** Sequential numbers (1, 2, 3...) become folder prefixes (1-, 2-, 3-...)

**LAYER 1 - Foundation (CRITICAL):**
1. [ ] 1-main-aspect-1 (Type: Data) - Blocks: all features - [0/6 sub-aspects]
2. [ ] 2-main-aspect-2 (Type: Foundational) - Blocks: user features - [0/4 sub-aspects]
3. [ ] 3-security-compliance (Type: Security) - Blocks: auth, API - [0/5 sub-aspects] *(if detected)*
4. [ ] 4-migration-legacy (Type: Migration) - Blocks: all work - [0/7 sub-aspects] *(if brownfield)*
5. [ ] 5-design-system (Type: UX) - Blocks: UI work - [0/8 sub-aspects]

**LAYER 2 - Infrastructure (HIGH):**
6. [ ] 6-main-aspect-3 (Type: Technical) - Depends: 1-main-aspect-1 - [0/3 sub-aspects]
7. [ ] 7-main-aspect-4 (Type: Integration) - Depends: 1-main-aspect-1, 2-main-aspect-2 - [0/5 sub-aspects]
8. [ ] 8-ai-ml (Type: AI/ML) - Depends: 6-main-aspect-3 - [0/5 sub-aspects] *(if detected)*

**LAYER 3 - Features (MEDIUM-HIGH):**
9. [ ] 9-main-aspect-5 (Type: Feature) - Depends: 6-main-aspect-3, 7-main-aspect-4 - [0/4 sub-aspects]
10. [ ] 10-main-aspect-6 (Type: Feature) - Depends: 6-main-aspect-3, 7-main-aspect-4 - [0/6 sub-aspects]

**LAYER 4 - Enhancements (MEDIUM-LOW):**
11. [ ] 11-main-aspect-7 (Type: Enhancement) - Depends: all features - [0/3 sub-aspects]
12. [ ] 12-main-aspect-8 (Type: Enhancement) - Depends: core features - [0/2 sub-aspects]

**Total:** [N] main aspects × [avg sub-aspects] = [~N total aspects to brainstorm]

**CURRENT POSITION:** [Status message]
- Completed: [list completed aspects] ✅
- In Progress: [list in-progress aspects] 🔄
- Next Up: [next aspect in sequence]

---

### 🎨 COLLABORATION SEQUENCE (User-First Workflow - NEW)

**Purpose:** Order aspects by user involvement need, enabling user-first brainstorming.

**PHASE 1: User-Led Creative/Strategic (High Involvement - Do First)**
*User's authentic voice, vision, and strategic decisions - deep collaborative dialogue*

1. [ ] [aspect-name] [Type: X] [📝 USER-CREATIVE] - [0/N sub-aspects]
   - Why first: Product differentiation/naming/brand identity/UX philosophy
   - User provides: Unique vision, authentic voice, creative direction
   - Dialogue: Open-ended exploration, capture user's ideas

2. [ ] [aspect-name] [Type: X] [🎯 USER-STRATEGIC] - [0/N sub-aspects]
   - Why first: Pricing/market/priority/risk decisions
   - User provides: Business strategy, tradeoff choices
   - Dialogue: Present options with analysis, facilitate decision

**PHASE 2: Claude-Led Informed/Autonomous (Low Involvement - After Phase 1)**
*Technical decisions informed by Phase 1 constraints + research-driven recommendations*

3. [ ] [aspect-name] [Type: X] [🤝 USER-INFORMED] - [0/N sub-aspects]
   - Why after Phase 1: Needs constraints from strategic aspects
   - Claude provides: Research + recommendations
   - User provides: Confirmation based on Phase 1 decisions
   - Dialogue: Present recommendation with rationale, get approval

4. [ ] [aspect-name] [Type: X] [⚡ CLAUDE-AUTONOMOUS] - [0/N sub-aspects]
   - Why after Phase 1: Standard best practices apply
   - Claude provides: Research → recommend
   - User provides: Rubber-stamp or raise concerns
   - Dialogue: Minimal, just confirmation

**Usage:**
- **Friend use case:** Do PHASE 1 only (creative/strategic), skip PHASE 2 (or just review recommendations)
- **Full workflow:** Complete Phase 1 first (establishes constraints), then Phase 2 (technical implementation)
- **Flexibility:** Can still follow Technical Sequence (dependency-based) if preferred

**Note:** This is ORTHOGONAL to Technical Sequence above. Choose based on preference:
- **Technical Sequence:** Respects dependencies (Foundation → Infrastructure → Features)
- **Collaboration Sequence:** Respects user time (Creative/Strategic first → Technical later)

---

### 🎯 WORKFLOW COMMAND MAPPING

**Which aspects feed into which VibeWiz workflow commands:**

- **/drd** (Data Requirements) → Read: main-aspect-1, [other Data aspects]
- **/tools** (Stack Selection) → Read: main-aspect-2, main-aspect-3, security-compliance, ai-ml, migration-legacy
- **/content** (Content Strategy) → Read: [Content aspects]
- **/ux-map** (UX Architecture) → Read: design-system, [all Feature aspects], [all UX aspects]
- **/ui** (Visual Templates) → Read: design-system, [Visual-Identity aspects]
- **/blueprint** (Component Architecture) → Read: design-system, [Component-Pattern aspects]
- **PRD-master** → Read: [all Feature aspects], [all Enhancement aspects]
- **/phases** → Read: ALL SUMMARY.md files, use dependency graph

---

### 🔒 CONDITIONAL ASPECTS DETECTION SUMMARY

**Security & Compliance:**
[If detected] ✅ AUTO-DETECTED based on:
- [List specific triggers: user accounts, sensitive data, payments, etc.]
[If not detected] ❌ No security aspects needed - [reason: static site/read-only/etc.]

**AI/ML:**
[If detected] ✅ AUTO-DETECTED based on:
- [List specific triggers: LLM integrations, vector search, AI features, etc.]
- Layer Placement: [LAYER 1 if core / LAYER 2 if supporting]
[If not detected] ❌ No AI/ML aspects needed - traditional application

**Migration/Legacy:**
[If detected] ✅ AUTO-DETECTED - BROWNFIELD PROJECT:
- Migrating from: [legacy system name]
- [List specific triggers: data migration, feature parity, etc.]
[If not detected] ❌ GREENFIELD PROJECT - no migration aspects needed

---
## 📚 DETAILED ASPECT DESCRIPTIONS (Read when brainstorming specific aspect)
---

**NOTE:** This section contains full details for each aspect. /brainstorm reads Quick Reference above for navigation, then jumps to specific aspect details here when actively brainstorming.

---

## LAYER 1: FOUNDATION (Priority: CRITICAL) 🧙‍♂️

*Must brainstorm FIRST - These are blocking dependencies*

### 1-[main-aspect-1]

**Type:** [Data/Foundational/UX/etc.] | **Collab:** [📝/🎯/🤝/⚡] | **Priority:** CRITICAL
**Deps:** None (foundation) | **Blocks:** [List aspects that depend on this]
**Subs:** [N] ([list sub-aspect names])
**Status:** [ ] Not started
**Feeds:** [/drd, /tools, /ux-map, etc.]

**📍 Compressed Format:** All questions, descriptions, integration details, and rationale are moved to this aspect's brainstorm-structure.md file (created by /brainstorm command). This section contains only essential metadata for navigation.

**🔗 When brainstorming:** /brainstorm reads this aspect's brainstorm-structure.md which contains:
- Complete problem domain description
- Detailed key questions to explore
- Sub-aspect breakdown with descriptions
- Integration points with other aspects
- WHAT to think about (not HOW to build)

---

### 2-[main-aspect-2]

[Same compressed format as above - repeat for all main aspects]

---

## LAYER 2: INFRASTRUCTURE (Priority: HIGH) 🏗️

*Brainstorm SECOND - These build on foundation to enable features*

### 3-[main-aspect-3]

[Same compressed format as above]

---

## LAYER 3: FEATURES (Priority: MEDIUM-HIGH) ⚡

*Brainstorm THIRD - These define core product functionality*

### 4-[main-aspect-4]

[Same compressed format as above]

---

## LAYER 4: ENHANCEMENTS (Priority: MEDIUM-LOW) ✨

*Brainstorm FOURTH - These enhance user experience and optimize*

### 5-[main-aspect-5]

[Same compressed format as above]

---
## END OF ASPECTS MAP
---


## Statistics

- **Main-Tier Aspects:** [N]
- **Sub-Aspects:** [N]
- **Sub-Sub-Aspects:** [N]
- **Total Aspects:** [N]
- **Maximum Depth:** [N] levels

**Type Breakdown:**
- Data: [N] aspects 🗄️
- Foundational/Technical: [N] aspects 🏗️
- Feature: [N] aspects ⚡
- Integration: [N] aspects 🔌
- UX/Design: [N] aspects 🎨
- Content: [N] aspects 📄
- Deployment: [N] aspects 🚀
- Security/Compliance: [N] aspects 🔒 *(if detected)*
- AI/ML: [N] aspects 🤖 *(if detected)*
- Migration/Legacy: [N] aspects 🔄 *(if brownfield)*
- Enhancement: [N] aspects ✨

---

## Next Steps

1. Begin brainstorming: `/brainstorm [project]`
   - Command auto-detects first aspect (first Foundation aspect)
   - Follow dependency order automatically
   - Run repeatedly - command navigates tree automatically
2. After each main aspect tree complete: `/evaluate-aspects [project] [main-aspect]`
3. After evaluation approval: `/summarize-aspect [project] [main-aspect]`
4. Repeat until all aspects complete
5. Proceed to /phases, /drd, /tools, /content, /ux-map, etc.
```

---

## Step 11: Update status.md

Add discovered aspects to status.md:

```markdown
## Current Step
Aspect brainstorming phase - progressing through [N] aspects:
**Foundation Layer:**
- [ ] [Main-Aspect-1] (Type: Data - CRITICAL)
- [ ] [Main-Aspect-2] (Type: Foundational - CRITICAL)
**Infrastructure Layer:**
- [ ] [Main-Aspect-3] (Type: Technical - HIGH)
**Feature Layer:**
- [ ] [Main-Aspect-4] (Type: Feature - MEDIUM-HIGH)
... (list all main-tier aspects only)
```

**Keep brief** - Main-tier aspects only with TYPE, tick off after completion

---

## Step 12: Output Summary

Report to user:
```
✅ **Aspect Tree Structure Created with Interactive Validation!**

**3 Gates Completed:**
- ✅ Gate 1: Main aspects identification approved
- ✅ Gate 2: Complete tree structure approved
- ✅ Gate 3: Final review & brainstorm plan approved

📊 Discovered Structure:
- Main-Tier Aspects: [N]
- Total Sub-Aspects: [N]
- Total Sub-Sub-Aspects: [N]
- Maximum Depth: [N] levels

🏷️ Type Distribution:
- Data Aspects: [N] 🗄️
- Foundational/Technical: [N] 🏗️
- Feature Aspects: [N] ⚡
- Integration Aspects: [N] 🔌
- UX/Design Aspects: [N] 🎨
- Content Aspects: [N] 📄
- Deployment: [N] 🚀
- Security/Compliance: [N] 🔒 *(if security triggers detected)*
- AI/ML: [N] 🤖 *(if AI/ML triggers detected)*
- Migration/Legacy: [N] 🔄 *(if brownfield project)*
- Enhancements: [N] ✨

🗂️ Files Created:
- aspects-map.md (complete brainstorming plan with TYPE metadata)
- [N] total empty folders with sequential numbering (1-, 2-, 1.1-, 1.2-, etc.)
  - Main aspects: 1-aspect-name, 2-aspect-name, 3-aspect-name...
  - Sub-aspects: 1.1-sub-name, 1.2-sub-name, 2.1-sub-name...
  - Recursive numbering to full depth (1.1.1-, 1.1.2-, etc.)
- Folder names sanitized (kebab-case, no special characters)
- 🚨 ZERO brainstorm-structure.md files (ALL handled by /brainstorm command)

📋 Dependency-Based Brainstorming Order:

LAYER 1 - Foundation (CRITICAL):
1. 1-[aspect-1] (Type: Data) - [N] aspects in tree
2. 2-[aspect-2] (Type: Foundational) - [N] aspects in tree

LAYER 2 - Infrastructure (HIGH):
3. 3-[aspect-3] (Type: Technical) - [N] aspects in tree
4. 4-[aspect-4] (Type: Integration) - [N] aspects in tree

LAYER 3 - Features (MEDIUM-HIGH):
5. 5-[aspect-5] (Type: Feature) - [N] aspects in tree
6. 6-[aspect-6] (Type: Feature) - [N] aspects in tree

LAYER 4 - Enhancements (MEDIUM-LOW):
7. 7-[aspect-7] (Type: Enhancement) - [N] aspects in tree

🔗 Workflow Integration:
Aspects are typed to feed specific workflow commands:
- Data aspects → /drd
- Technical aspects → /tools, architecture.md
- Security aspects → /tools, architecture.md, PRD security requirements *(if detected)*
- AI/ML aspects → /tools, architecture.md, PRD AI features *(if detected)*
- Migration aspects → /phases, /tools, architecture.md *(if brownfield)*
- Feature aspects → PRD-master, /summary
- UX aspects → /ux-map, /ui, /blueprint
- Content aspects → /content
- (See aspects-map.md for complete mapping)

🔒 Conditional Aspects Detection:

**Security & Compliance:**
[If detected] AUTO-DETECTED based on:
- User accounts/authentication required
- Sensitive data handling (PII, health, financial)
- Payment processing
- API security needs
- [List specific triggers found]
[If not detected] No security aspects needed - project is [static site/read-only content/etc.]

**AI/ML:**
[If detected] AUTO-DETECTED based on:
- LLM integrations (GPT, Claude, etc.)
- Machine learning models
- AI-generated content
- Vector databases/semantic search
- [List specific triggers found]
[If not detected] No AI/ML aspects needed - traditional application

**Migration/Legacy:**
[If detected] AUTO-DETECTED - BROWNFIELD PROJECT:
- Migrating from: [legacy system]
- Data migration required
- Feature parity considerations
- [List specific migration triggers found]
[If not detected] GREENFIELD PROJECT - no migration aspects needed

🚀 Next Step:
/brainstorm [project]

The /brainstorm command will auto-detect position, create structures dynamically, and navigate the tree autonomously. Just run it repeatedly!

See aspects-map.md for complete planning details! ✨🧙‍♂️
```

## Key Principles

### Interactive Collaborative Planning
- **3 Approval Gates**: Main aspects → Tree structure → Final review
- **Up to 3 iterations per gate**: User can refine until satisfied
- **User expertise injection**: Domain knowledge beats AI assumptions
- **Early gap detection**: Find missing aspects at Gate 1 vs discovering mid-brainstorm
- **Appropriate depth validation**: Ensure sub-aspects go deep enough at Gate 2
- **Confident execution**: User ready to proceed after Gate 3

### Complete Structure Upfront
- User sees full scope immediately with TYPE classifications
- No structural surprises during planning
- Clear roadmap from start to finish with dependency rationale
- "Structure First, Context Later" philosophy maintained

### NO Structure Files (Moved to /brainstorm)
- ONLY folders created by /aspects
- /brainstorm creates brainstorm-structure.md dynamically with context
- Avoids redundant upfront work

### Comprehensive TYPE Metadata
- Every aspect categorized by TYPE
- Types feed into specific workflow commands
- Ensures comprehensive coverage for entire VibeWiz flow

### Dependency-Aware Ordering
- Foundation aspects first (blocking dependencies - CRITICAL)
- Infrastructure second (builds on foundation - HIGH)
- Features third (core product - MEDIUM-HIGH)
- Enhancements fourth (optimizations - MEDIUM-LOW)
- Clear LAYER system with dependency graph

### Extensive Ultra-Thinking
- 15-30+ sequential thinks for proper categorization
- Consider all aspect TYPES (Data/Foundational/Feature/Integration/UX/Content/Deployment/Enhancement)
- Conditional detection (Security/AI-ML/Migration)
- Analyze dependencies deeply
- Map to downstream workflow needs

## Success Criteria

A successful aspects analysis:
- [ ] **Completes 3 interactive approval gates:**
  - [ ] Gate 1: Main aspects identification approved (up to 3 iterations)
  - [ ] Gate 2: Complete tree structure approved (up to 3 iterations)
  - [ ] Gate 3: Final review & brainstorm plan approved (up to 3 iterations)
- [ ] Analyzes exploration-initial.md (or project-core.md if exists) thoroughly
- [ ] Uses EXTENSIVE ultra-thinking (15-30+ thinks) for main aspects AND sub-aspects
- [ ] Categorizes ALL aspects by TYPE (Data/Foundational/Feature/UX/Content/Deployment/Enhancement)
- [ ] Categorizes ALL aspects by COLLABORATION-TYPE (USER-CREATIVE/USER-STRATEGIC/USER-INFORMED/CLAUDE-AUTONOMOUS)
- [ ] **Detects conditional aspects intelligently:**
  - [ ] Security & Compliance (if user accounts, sensitive data, payments, compliance)
  - [ ] AI/ML (if LLMs, ML models, AI-generated content, vector search)
  - [ ] Migration/Legacy (if brownfield/replacement project, NOT greenfield)
- [ ] Identifies all main-tier aspects (typically 6-15 depending on complexity)
- [ ] Detects sub-aspects for each main aspect (typically 3-8 each)
- [ ] Identifies sub-sub-aspects where needed (recursive depth)
- [ ] **User validates completeness and depth at each gate**
- [ ] Creates complete folder tree structure (NO structure files)
- [ ] Creates comprehensive aspects-map.md with:
  - [ ] TYPE metadata for every aspect
  - [ ] COLLABORATION-TYPE for workflow ordering
  - [ ] Conditional aspect detection reasoning (why included/excluded)
  - [ ] Dependency graph with LAYER system
  - [ ] Workflow command mapping (which aspects feed which commands)
  - [ ] Complete brainstorming order with rationale
- [ ] Determines dependencies accurately
- [ ] Prioritizes aspects by dependency layers
- [ ] Updates status.md with TYPE info
- [ ] Outputs summary with gate completion confirmation

## Important Notes

- **Interactive Workflow**: 3 approval gates with up to 3 iterations each
- Run this command ONLY ONCE per project (after /explore)
- Creates entire folder structure upfront (no incremental discovery)
- **User actively shapes the aspect structure** through gate approvals
- **🔢 Sequential Numbering:** ALL folders include numbering prefix (1-, 2-, 1.1-, 1.2-, etc.)
  - Based on brainstorming order from aspects-map.md
  - Continues recursively to all depth levels
  - Enables clear navigation and dependency tracking
- **🧹 Folder Name Sanitization:** All folder names cleaned (kebab-case, no special characters)
  - Removes: `{ } [ ] ( ) < > " ' / \ | ? * : ;`
  - Ensures filesystem compatibility across all platforms
- NO brainstorm-structure.md files created (ALL structure files moved to /brainstorm for dynamic creation)
- aspects-map.md is the planning bible (refer to it constantly)
- Follow brainstorming order strictly (respects dependency layers)
- Use EXTENSIVE ultra-thinking (15-30+ thinks minimum) for TYPE analysis
- **Conditional Aspect Detection:** 3 special types with smart detection:
  - Security & Compliance 🔒 (detect: auth, sensitive data, payments, compliance)
  - AI/ML 🤖 (detect: LLMs, ML models, vector search, AI features)
  - Migration/Legacy 🔄 (detect: brownfield ONLY, replacing existing systems)
- NO SCOPE LIMITS: Could be 5 main aspects or 50, could be 20 total aspects or 500
- NO DEPTH LIMITS: Go to 2 levels, 3, 4, 5, 6+ levels - whatever the project needs
- Embrace FULL scope - this enables true one-shot vibecoding
- TYPE metadata ensures comprehensive VibeWiz workflow coverage

## Integration with Workflow

```
1. /explore [project]        → exploration-initial.md
2. /aspects [project]        → COMPLETE structure + aspects-map.md (NO structure files)
3. /brainstorm [project]     → Auto-navigate tree, create structures dynamically
   (Run repeatedly - command handles navigation automatically)
4. /evaluate-aspects [...]   → After each main aspect complete
5. /summarize-aspect [...]   → After evaluation approval
6. Repeat 3-5 for all main aspects
7. /drd, /tools, /content, /ux-map, etc. → Read typed SUMMARY.md files
8. /phases, /summary, etc.   → Use ALL SUMMARY.md files
```

## Ultra-Thinking Prompts for TYPE Analysis

Use 15-30+ sequential thinks during Step 3 to analyze:

**1. Scope & Domains**
- Major planning domains in this project?
- Areas needing deep architectural planning?
- Cross-cutting concerns (security, performance, data)?
- Problems to solve (NOT technologies to use)?

**2. TYPE Classification**
- Data: Database models, schemas, validation rules
- Foundational: Core architecture, auth, security, infrastructure
- Feature: User-facing functionality, business logic
- Integration: Third-party APIs, external services, webhooks
- UX: Visual identity, flows, components, layout, accessibility
- Content: Content types, sources, media, CMS, localization
- Deployment: CI/CD, monitoring, scaling
- Enhancement: Optimizations, analytics, nice-to-haves

**3. Conditional Detection (Add ONLY if triggers found)**
- **Security 🔒:** User accounts? Sensitive data? Payments? APIs? Multi-tenant? → Add to LAYER 1
- **AI/ML 🤖:** LLMs? ML models? Vector search? AI-generated content? → LAYER 1 (core) or LAYER 2 (supporting)
- **Migration 🔄:** Brownfield (replacing existing)? Legacy data? → Add to LAYER 1 | Skip if greenfield (new)

**4. UX Auto-Detection**
- User-facing app? → Comprehensive UX tree (Visual, Flows, Components, Layout, A11y) in LAYER 1
- Developer-facing? → Minimal UX (CLI/API docs)
- Backend-only? → Skip UX

**5. Breakdown & Dependencies**
- Sub-aspects? Sub-sub-aspects? Go deeper until actionable
- Foundation (blocks all) → Infrastructure (needs foundation) → Features (needs infrastructure) → Enhancements (needs features)

**6. Workflow Integration**
- Which aspects feed /drd? (Data types)
- Which feed /tools? (Foundational, Integration, Security, AI/ML, Migration)
- Which feed /content? (Content types)
- Which feed /ux-map? (UX + Feature types)
- Which feed PRD? (Feature + Enhancement types)

**7. Anti-Patterns (AVOID)**
- ❌ Specific APIs/services (use generic names)
- ❌ HOW to build (describe WHAT problem)
- ❌ Implementation details (save for brainstorming)
- ❌ Technology choices (come from /brainstorm, /tools)

**Remember:** Ask "Does this need X?" not "How to implement X?" | Structure first, solutions later.

## Visual-Identity Brainstorming (Ideation-Based Design)

**Philosophy:** Extract PRINCIPLES from references → Create ORIGINAL solutions for this project

**Ideation Tree Model:**
- **ROOT:** Project vision, user expectations, industry context
- **TRUNK:** Core design principles (3-5 decisions that drive everything)
- **BRANCHES:** Design dimension choices (typography, color, spacing, layout)
- **LEAVES:** Specific implementations (font pairings, hex codes, component styles)

**Process:**
1. **Gather references** (/references/design-examples/) - NO extraction yet
2. **Exploratory dialogue** - Project personality? User emotions? Brand adjectives?
3. **Principles synthesis** - What guidelines emerge? (3-5 core principles)
4. **Dimension exploration** - For each principle, explore dimensions (color, type, space, etc.)
5. **Concrete proposals** - Specific implementations that embody principles
6. **Iterative refinement** - User feedback → adjust → converge

**Key Questions for Visual-Identity:**
- **Personality:** What 3-5 adjectives describe the visual tone?
- **References:** Which sites capture the VIBE? (for principles, not copying)
- **Typography:** Scale ratio (1.200 balanced / 1.333 editorial / 1.500 bold)?
- **Color:** Warm/cool? Vibrant/muted? Primary color count (1-3)?
- **Spacing:** Compact (information-dense) or generous (breathing room)?

**Key Questions for User-Flows:**
- **Navigation:** How do users move between major sections?
- **User journeys:** What are the 3-5 critical paths?
- **State management:** How does UI reflect system state?
- **Error handling:** How do we guide users when things go wrong?

**Key Questions for Layout-Architecture:**
- **Grid system:** Fixed-width or fluid? Column count?
- **Hierarchy:** How do we establish visual importance?
- **Responsive strategy:** Mobile-first? Breakpoint approach?
- **Composition:** Asymmetric (dynamic) or symmetric (balanced)?

**Output:** Original design tailored to THIS project, informed by (not copied from) references.

**Reference:** See `/references/design-system-philosophy.md` for complete ideation methodology.

---

**Note:** Claude synthesizes principles from references + user vision, then creates original solutions. Transform from COPIER → CREATIVE DESIGNER.
