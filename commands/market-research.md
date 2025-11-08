---
description: Launch extensive market research on similar projects and competitors
argument-hint: [project-name]
---

# Market Research Command - Competitive Intelligence & Strategic Positioning

## Objective
Conduct comprehensive market research after initial exploration to discover competitors, similar projects, pricing models, feature sets, tech stacks, user feedback, and market opportunities. This intelligence informs aspects creation and strategic differentiation.

## Philosophy
**Know The Battlefield:**
- Deep understanding of competitive landscape
- Identify what works and what doesn't
- Discover market gaps and opportunities
- Learn from others' successes and failures
- Position project strategically

**Extensive Investigation:**
- 8-10+ parallel web searches minimum
- Multiple perspectives on each category
- Real user feedback and pain points
- Current market trends and pricing
- Technical implementation patterns

## Command Structure

```bash
/market-research [project-name]

# Examples:
/market-research nutri
/market-research digital-grimoire
/market-research mg-enthusiast
```

## Process

### 1. Parse and Validate

- Extract project name from arguments
- Verify project exists at `/home/kodd/VibeWiz/Projects/[project-name]/`
- Confirm `exploration-initial.md` exists
- Ensure market research hasn't been run yet (or confirm re-run)

### 2. Read Exploration Document

Read `.wiz/exploration/exploration-initial.md`:
- Understand project vision and scope
- Extract key concepts and keywords
- Identify project type/category
- Determine target market and users
- Note unique value propositions mentioned

### 3. Launch General-Purpose Agent

Spawn a general-purpose agent with the following task:

**Agent Instructions:**
```
You are conducting extensive market research for the [project-name] project.

IMPORTANT: Launch ALL web searches in PARALLEL using a single message with multiple WebSearch tool calls. This is a VibeWiz requirement - we maximize parallelization.

Read the exploration document at: /home/kodd/VibeWiz/Projects/[project-name]/.wiz/exploration/exploration-initial.md

Based on the exploration, conduct comprehensive market research across these categories:

1. **Direct Competitors** (2-3 searches)
   - Main competitors in this space
   - Leading products/platforms
   - Dominant players and market leaders

2. **Alternative Solutions** (1-2 searches)
   - Adjacent/alternative approaches
   - Different ways users solve this problem
   - Substitute products

3. **Pricing & Monetization** (1-2 searches)
   - Pricing models in this space
   - Subscription vs one-time vs freemium
   - Revenue strategies and business models

4. **Feature Analysis** (2-3 searches)
   - Common features across competitors
   - Differentiating features
   - Feature gaps and unmet needs

5. **Technical Implementation** (1-2 searches)
   - Tech stacks commonly used
   - Architecture patterns
   - Technical challenges in this domain

6. **User Feedback & Pain Points** (2-3 searches)
   - User reviews and complaints
   - Reddit/forum discussions
   - What users love and hate
   - Unmet needs and frustrations

7. **Market Trends** (1-2 searches)
   - Industry trends and directions
   - Emerging technologies in this space
   - Market size and growth

8. **Success Factors** (1-2 searches)
   - What makes competitors successful
   - Key differentiators that work
   - Lessons from failures

REMEMBER: Launch ALL these searches in PARALLEL in a single message. Aim for 10-15 total searches covering all categories above.

After gathering all research, synthesize findings into a comprehensive market-research.md document.

Output Location: /home/kodd/VibeWiz/Projects/[project-name]/.wiz/exploration/market-research.md

Document Structure:

# Market Research: [Project Name]

*Generated: [date]*
*Based on: exploration-initial.md*

---

## Executive Summary

[2-3 paragraph overview of market landscape, key findings, and strategic implications]

---

## 1. Competitive Landscape

### Direct Competitors

#### [Competitor 1 Name]
- **Website:** [URL]
- **Description:** [What they do]
- **Strengths:** [What they do well]
- **Weaknesses:** [Where they fall short]
- **Target Market:** [Who they serve]
- **Pricing:** [Pricing model and tiers]

#### [Competitor 2 Name]
[Same structure]

### Alternative Solutions

[Products/approaches that solve the problem differently]

---

## 2. Feature Comparison Matrix

| Feature Category | [Competitor A] | [Competitor B] | [Competitor C] | **Our Opportunity** |
|-----------------|----------------|----------------|----------------|---------------------|
| [Core Feature 1] | ✅ | ✅ | ❌ | [Insight] |
| [Core Feature 2] | ⚠️ Limited | ✅ | ✅ | [Insight] |
| [Unique Feature] | ❌ | ❌ | ❌ | ✅ **Gap!** |

---

## 3. Pricing Analysis

### Common Pricing Models
- [Model 1]: [Description, pros/cons, who uses it]
- [Model 2]: [Description, pros/cons, who uses it]

### Pricing Tiers Observed
| Tier | Price Range | Typical Features | Target User |
|------|-------------|------------------|-------------|
| Free | $0 | [Features] | [User type] |
| Basic | $X-Y/mo | [Features] | [User type] |
| Pro | $X-Y/mo | [Features] | [User type] |
| Enterprise | Custom | [Features] | [User type] |

### Recommended Strategy
[Based on market analysis, what pricing approach makes sense]

---

## 4. Technical Stack Analysis

### Common Technologies
- **Frontend:** [What competitors use]
- **Backend:** [What competitors use]
- **Database:** [What competitors use]
- **Infrastructure:** [Hosting, CDN, etc.]

### Technical Challenges in This Domain
1. [Challenge 1 and how competitors address it]
2. [Challenge 2 and how competitors address it]

### Technical Opportunities
- [Areas where better tech could provide advantage]

---

## 5. User Feedback & Pain Points

### What Users Love
- ✅ [Common praise across products]
- ✅ [Features users appreciate]
- ✅ [Experiences users value]

### What Users Hate
- ❌ [Common complaints]
- ❌ [Frequent frustrations]
- ❌ [Unmet needs]

### Quote Highlights
> "[Actual user quote from Reddit/reviews]" - [Source]

> "[Another revealing quote]" - [Source]

### Synthesized User Needs
1. **[Need 1]:** [What users are asking for but not getting]
2. **[Need 2]:** [Another unmet need]

---

## 6. Market Gaps & Opportunities

### Identified Gaps
1. **[Gap 1]:** [Description of what's missing in market]
   - **Evidence:** [Why we believe this is a gap]
   - **Opportunity:** [How we could fill it]

2. **[Gap 2]:** [Description]
   - **Evidence:** [Why]
   - **Opportunity:** [How]

### Underserved Markets
- [Market segment 1]: [Why underserved, opportunity size]
- [Market segment 2]: [Why underserved, opportunity size]

---

## 7. Differentiation Strategy

### Our Unique Positioning
Based on market analysis, we can differentiate through:

1. **[Differentiator 1]:** [How this sets us apart]
   - **Competitors' Approach:** [What they do]
   - **Our Approach:** [What we'll do differently]
   - **User Benefit:** [Why users will care]

2. **[Differentiator 2]:** [How this sets us apart]
   [Same structure]

### Competitive Advantages
- [Advantage 1 we can leverage]
- [Advantage 2 we can leverage]

---

## 8. Success Factors

### What Makes Competitors Successful
1. [Factor 1]: [Why it works]
2. [Factor 2]: [Why it works]

### What Makes Competitors Fail
1. [Factor 1]: [Why it hurts them]
2. [Factor 2]: [Why it hurts them]

### Lessons Applied
- **Do:** [What we should emulate]
- **Don't:** [What we should avoid]
- **Innovate:** [Where we should do something new]

---

## 9. Market Trends

### Current Trends
- [Trend 1]: [Description and implications]
- [Trend 2]: [Description and implications]

### Emerging Technologies
- [Tech 1]: [How it's being adopted in this space]
- [Tech 2]: [How it's being adopted in this space]

### Future Outlook
[Where the market is heading, opportunities on the horizon]

---

## 10. Strategic Recommendations

### Phase 1 Priorities (Must-Haves)
1. [Feature/capability based on market research]
2. [Feature/capability based on market research]

### Phase 2 Enhancements (Differentiators)
1. [Feature that sets us apart]
2. [Feature that sets us apart]

### Phase 3 Innovation (Market Leadership)
1. [Innovative feature no competitor has]
2. [Innovative feature no competitor has]

### Avoid These Mistakes
- ❌ [Common mistake observed in competitors]
- ❌ [Another mistake to avoid]

---

## 11. Research Sources

### Competitor Websites
- [Competitor 1]: [URL]
- [Competitor 2]: [URL]

### User Feedback Sources
- [Reddit thread/subreddit]: [URL]
- [Review site]: [URL]

### Industry Analysis
- [Article/report]: [URL]
- [Market research]: [URL]

---

## Next Steps

1. **Review Findings:** Discuss strategic implications with team
2. **Refine Positioning:** Use insights to sharpen our unique value proposition
3. **Inform Aspects:** Let market gaps guide /aspects planning priorities
4. **Validate Assumptions:** Use competitor analysis to validate/challenge exploration assumptions
5. **Update Exploration:** Consider updating exploration-initial.md with market insights

This research should significantly inform the /aspects command and subsequent brainstorming sessions.
```

### 4. Update status.md

After market research completes, update status.md:

```markdown
## Current Step
Market research complete - analyzed competitive landscape, pricing models, and market gaps. Ready for /aspects.

## History
- [date] - Initial exploration completed
- [date] - Market research conducted ([N] competitors analyzed)
- Next: /aspects to create planning structure
```

### 5. Output Summary

Report to user when complete:

```
✅ Market Research Complete!

📊 Analysis Summary:
- Competitors Analyzed: [N]
- Market Gaps Identified: [N]
- User Pain Points Discovered: [N]
- Differentiation Opportunities: [N]

🎯 Key Findings:
1. [Major insight 1]
2. [Major insight 2]
3. [Major insight 3]

📁 Report Location:
Projects/[project-name]/.wiz/exploration/market-research.md

🚀 Next Step:
Review the market research document, then run:
/aspects [project-name]

The market insights will help inform aspect priorities and strategic decisions during brainstorming.
```

## Key Principles

### Extensive Investigation
- 10-15+ web searches minimum
- Cover all categories comprehensively
- Multiple search angles per category
- Real user feedback is critical

### Parallel Execution
- ALL searches in single message
- Maximize efficiency via parallelization
- Follows VibeWiz parallelization rules

### Actionable Insights
- Not just data collection
- Clear strategic implications
- Specific differentiation opportunities
- Practical recommendations

### Integration with Workflow
- Informs /aspects priorities
- Guides differentiation strategy
- Validates exploration assumptions
- Shapes feature planning

## Success Criteria

A successful market research session:
- [ ] Reads exploration-initial.md thoroughly
- [ ] Launches 10-15+ parallel web searches
- [ ] Analyzes 5+ direct competitors
- [ ] Identifies 3+ market gaps
- [ ] Documents 10+ user pain points
- [ ] Creates comprehensive pricing analysis
- [ ] Reviews technical implementation patterns
- [ ] Synthesizes findings into strategic recommendations
- [ ] Generates complete market-research.md document
- [ ] Updates status.md
- [ ] Provides clear next steps

## Important Notes

- Run this command AFTER /explore, BEFORE /aspects
- Optional but highly recommended for competitive markets
- Can be re-run if market changes significantly
- Agent will conduct 10-15+ searches in parallel (follows VibeWiz rules)
- Focus on actionable insights, not just data collection
- Look for both what competitors do well AND where they fail
- User feedback is gold - prioritize finding real user voices

## Integration with Workflow

```
1. /explore [project]              → exploration-initial.md
2. /market-research [project]      → market-research.md (competitive intelligence)
3. /aspects [project]              → Use market insights to inform priorities
4. /brainstorm [...]               → Reference market gaps for differentiation
5. Continue workflow...
```

## When to Skip

Skip market research if:
- Building something truly novel (no competitors)
- Internal tool (not competing in market)
- Already deeply familiar with competitive landscape
- Rapid prototyping phase (can do later)

## When to Re-Run

Re-run market research when:
- Major competitor launches new features
- New competitors enter market
- Pivoting project direction
- Preparing for major strategic planning
- 6+ months since last research
