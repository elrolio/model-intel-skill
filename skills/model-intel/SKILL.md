---
name: model-intel
description: Day-one intelligence gathering for newly released AI models (LLMs, generative media)
---

Execute comprehensive day-one intelligence gathering for the model the user named. If they have not
named one, ask which model before doing anything else.

**Scope**: LLMs and generative media models only (text, image, video, audio generation models)

**Timeframe**: Conduct research within 8 hours of this command execution (real-time signal capture)

**Output**: Single consolidated intelligence report at `intel/competitive/[model-name-slug]-launch-intelligence-[YYYY-MM-DD].md`

**Methodology Reference**: `frameworks/intelligence/day-one-model-intelligence-methodology.md`

---

## Research Protocol

### Phase 1: Launch 5 Parallel Research Agents (Single Message)

Execute these agents simultaneously in ONE message with multiple Task tool calls:

1. **Twitter/X Vibe Agent**
   - Focus: Vibe checks, first impressions, developer reactions
   - Tool: Use **TWITTER_RECENT_SEARCH** via Rube MCP (not WebSearch)
   - Query: `"[Model Name]" OR "[model-slug]" -is:retweet` with `start_time` set to launch day
   - Parameters: `max_results: 100`, `sort_order: "relevancy"`, `tweet_fields: ["created_at", "public_metrics"]`, `expansions: ["author_id"]`, `user_fields: ["public_metrics", "verified"]`
   - Capture: High-engagement tweets with exact metrics (like_count, retweet_count, quote_count), author info (verified status, follower count), theme frequency
   - Track: Top 5-7 themes (speed, coding, reasoning, cost, multimodal, etc.)
   - Note: impression_count returns 0 for others' tweets - use like/retweet counts for engagement filtering

2. **Technical Blog Agent**
   - Focus: Deep dives, benchmark analysis, expert commentary
   - Sources: Artificial Analysis, Apidog, technical blogs, independent researchers
   - Capture: Benchmark validation (independent > vendor claims), architectural details, performance analysis

3. **Community Forum Agent**
   - Focus: Hacker News, Reddit (r/LocalLLaMA, r/MachineLearning, r/singularity)
   - Analyze: Developer technical discussions, skepticism patterns, implementation concerns
   - Note: Early activity level as market signal

4. **Video/Creator Agent**
   - Focus: YouTube demos, creator first looks, hands-on testing
   - Capture: What creators showcase, demo capabilities, practical observations
   - Note: May have limited day-one content (acknowledge in report)

5. **Enterprise Testimonial Agent** (Dedicated - Non-Blocking)
   - Focus: Company case studies, production metrics, press releases
   - Proactively search: Official launch partners, beta tester announcements, enterprise blog posts
   - Capture: Real production metrics (% improvements, cost savings, use case validation)
   - **Critical**: Run independently so case study hunting doesn't bottleneck main synthesis

### Phase 2: Direct Searches (If Needed - Usually Covered by Agents)

Agents above should handle most research. Only use direct searches if agents miss critical sources:
- News coverage (via WebSearch if not covered)
- Reddit search (REDDIT_SEARCH if not covered by Community Forum Agent)

**Note**: Twitter/X search should be handled by Twitter/X Vibe Agent using TWITTER_RECENT_SEARCH, not as a separate Phase 2 step.

---

## Audience & Purpose

**Primary readers**: Product/Engineering teams conducting evals and testing pre-ship + Marketing for pulse check

**Core questions to answer**:
- What should we test? (Product/Eng)
- What's working? What's broken? (Product/Eng)
- What's the narrative? What's landing? (Marketing)

**NOT**: Strategic competitive analysis (separate doc, post-testing)

---

## Output Structure: VIBES + DEETS

### Executive Summary

**Required elements**:
- Release date and positioning statement
- 3 standout capabilities (community consensus on what it's good at)
- 3 major concerns (what people are worried about)
- One-line market positioning (optional)

**Max length**: 3 paragraphs (150-200 words)

---

### THE VIBES Section
*Social media reactions, community sentiment (Twitter/X, Reddit)*

**What People Are Hyped About**:
- Top themes by frequency (with % of tweets mentioning)
- High-engagement quotes with attribution (@username, like/RT counts)
- Specific use cases and applications mentioned
- What resonates with community

**What People Are Concerned About**:
- Critiques and skepticism (with attribution)
- Red flags identified
- Trust/reliability concerns
- Pricing/cost trajectory worries
- Benchmark fatigue signals

**Community Pulse** (compress to 1 paragraph):
- HN/Reddit/forum activity with one key signal
- Overall sentiment (qualitative, not precise percentages)

**Editorial rules**:
- Quote with attribution and engagement metrics
- Identify themes by frequency
- Note what's surprisingly absent
- No prescriptive guidance
- Max 2-3 sentences per point
- **Avoid**: Media narrative analysis (not decision-critical), verbose community breakdowns, sentiment percentages

---

### THE DEETS Section
*Technical analysis, enterprise validation, production metrics (Hacker News, blogs, enterprise)*

**Verified Performance Strengths**:
- Benchmark performance (independent validation preferred over vendor claims)
- Enterprise production metrics (real numbers from real companies)
- Speed/latency measurements
- Architecture details (adaptive computation, thinking modes, etc.)
- Applications validated in production

**Critical Technical Limitations**:
- Performance trade-offs (speed vs. quality, cost vs. capability)
- Technical issues reported (bugs, gaps, migration friction)
- Feature gaps vs. competitors
- Hidden costs (token consumption patterns, pricing increases)
- Production concerns (hallucination, reliability, privacy)

**Editorial rules**:
- Enterprise metrics with company attribution
- Independent validation > vendor benchmarks
- Distinguish claims from validated measurements
- Technical precision
- No speculation
- **Avoid**: Separate "Applications in Production" subsection (redundant with testimonials), "Architecture Innovations" deep-dives (redundant with capabilities), "Platform Availability" lists (covered in Tech Specs)

---

### Competitive Positioning (Collapsed Toggle - "for Marketing")

**Market Strategy**:
- Distribution approach
- Pricing positioning
- Launch timing implications

**vs. Claude / OpenAI / Open Source**:
- Community perception (one paragraph each)
- Structural advantages/disadvantages

**Purpose**: Marketing context for model picker messaging, GTM positioning (NOT day-one engineering decision support)

---

### Strategic Implications (Collapsed Toggle - "for GTM Planning")

**3-4 key reads** (1 paragraph each):
1. Distribution/positioning strategy
2. Trust/credibility dynamics
3. Cost implications

**Purpose**: Post-testing strategic planning (NOT pre-ship decision support)

**Editorial rule**: Present strategic reads, don't prescribe action. Collapse by default in Notion - this is for later GTM work.

---

### Key Unknowns

**5-7 questions** the research can't answer yet:
- What hasn't been tested
- What needs more time
- When to revisit (7-14 days typically)

---

### Methodology (Collapsed Toggle)

One-line summary: "Research: 5 agents, X hrs post-launch, ~N sources. Verification: URLs verified, testimonials exact match."

**Collapse by default in Notion** - verification detail isn't scan-critical.

---

### Sources

**Organized by category**:
- Official (company blogs, documentation)
- News (major outlets with links)
- Technical Analysis (independent researchers, blogs)
- Community (Hacker News threads, Reddit)
- Enterprise (if found)

**Format**: Compact with inline links

---

## Anti-Redundancy Rules

**Single source of truth for each fact**:
- Architecture details (Adaptive Thinking, Agent Teams) → mentioned ONCE in "What People Are Hyped About," NOT repeated in separate "Architecture Innovations" section
- Financial metrics → in Enterprise Validation table, NOT separate "Financial Services Deep Dive"
- Platform availability → in Technical Specifications table, NOT separate list
- Sentiment → qualitative in "Community Pulse," NOT percentages in separate section
- Media strategy → one sentence in Community Pulse if relevant, NOT separate "Media Narrative" section

**Collapse by default (for optional depth)**:
- Competitive Positioning → Toggle "for Marketing"
- Strategic Implications → Toggle "for GTM Planning"
- Methodology → Toggle with one-line summary
- Sources → Toggle (always at end)

**What NOT to Include**:
- ❌ "What to look for in your evals" sections
- ❌ "Recommended next steps" for testing
- ❌ Prescriptive recommendations on model usage
- ❌ Generic observations without signal
- ❌ Duplication between VIBES and DEETS sections
- ❌ Speculation about future capabilities

**Principle**: Intelligence > Advice. Diagnostic > Strategic. Report what works/breaks for testing, defer positioning analysis to collapsed sections.

---

## Editorial Standards

**Structure**:
- VIBES first (social sentiment)
- DEETS second (technical validation)
- Clear sourcing categories throughout
- No duplication between sections
- Max 2-3 sentences per paragraph

**Tone**:
- Direct, professional
- No AI voice patterns
- Present findings, don't editorialize
- Quote sources with attribution and engagement metrics
- Distinguish claims vs. validated measurements

**Synthesis Quality**:
- Consolidate similar points under single themes
- Highlight what's surprisingly absent
- Note coverage gaps honestly
- Strategic reads at end (distribution, trust, pressure, cost)

---

## Success Criteria

Report should enable reader to quickly understand:
1. What the community consensus says the model is good at
2. What concerns have emerged
3. How it's positioned competitively
4. What remains unknown/untested

Report should NOT:
1. Tell reader how to test or evaluate the model
2. Prescribe next steps or actions
3. Repeat information between sections
4. Include generic observations without signal

---

**Execute this research protocol now for the model specified above.**