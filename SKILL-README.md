# /model-intel - AI Model Launch Intelligence Skill

Day-one intelligence gathering for newly released AI models (LLMs, generative media). Produces structured VIBES + DEETS reports within hours of launch.

## Quick Start

1. **Copy skill file**: `model-intel.md` → `~/.claude/skills/model-intel/SKILL.md`
2. **Optional**: Install Rube MCP for enhanced Twitter/X coverage (see Setup Guide)
3. **Run**: `claude "/model-intel [Model Name]"`

## What You Get

Comprehensive intelligence report covering:
- Social sentiment (Twitter, Reddit, HN)
- Technical benchmarks (independent validation)
- Enterprise testimonials and production metrics
- Competitive positioning
- Key unknowns for future research

**Example**: [Claude Opus 4.6 Report](https://www.notion.so/descript/Claude-Opus-4-6-Launch-Intelligence-Feb-5-2026-2feabe2e1a508193a1d4cb8aff3754d5)

## Installation Options

### Minimal (Built-in Tools Only)
- ✅ Works immediately with Claude Code
- ✅ No additional setup required
- ⚠️ Twitter coverage limited to web search
- ⚠️ Lower data quality on social sentiment

### Recommended (With Rube MCP)
- ✅ Twitter/X direct API access
- ✅ Enhanced web scraping (Firecrawl)
- ✅ Structured social media data
- ⚠️ Requires Composio account (free tier available)

**Install Rube**: See `model-intel-setup-guide.md` for complete instructions.

## Usage Examples

**Initial pulse** (within 8 hours of launch):
```bash
claude "/model-intel GPT-5 Pro"
```

**Afternoon update** (12-16 hours later):
```bash
claude "/model-intel afternoon update for GPT-5 Pro. morning report: [URL]"
```

**Specify output location**:
```bash
claude "/model-intel Sora 2.0 - save to projects/intel/"
```

## Dependency Matrix

| Tool/MCP | Required? | Purpose | Alternative |
|----------|-----------|---------|-------------|
| Task tool | ✅ Yes | Spawn parallel agents | None |
| research-orchestration-agent | ⚠️ Recommended | Specialized research agent | general-purpose agent |
| Rube MCP | ⚠️ Recommended | Twitter/X API, web scraping | WebSearch, WebFetch |
| WebSearch | ✅ Yes (built-in) | Fallback web research | N/A |
| WebFetch | ✅ Yes (built-in) | Fallback page scraping | N/A |
| Notion MCP | ⬜ Optional | Publish to Notion | Manual copy/paste |
| Memory MCP | ⬜ Optional | Session context storage | Skip memory_ingest calls |

## Files Included

```
model-intel/
├── SKILL.md                    # Main skill file (install to ~/.claude/skills/)
├── README.md                   # This file (quick reference)
├── model-intel-setup-guide.md  # Complete installation instructions
└── examples/
    └── claude-opus-4-6-launch-intelligence-2026-02-05.md  # Example output
```

## Output Structure

Reports follow this format:
1. **Executive Summary** (3 paragraphs)
2. **THE VIBES** (social media reactions)
   - What People Are Hyped About
   - What People Are Concerned About
   - Community Pulse
3. **THE DEETS** (technical analysis)
   - Technical Specifications
   - Verified Performance Strengths
   - Critical Technical Limitations
   - Enterprise Validation
4. **Competitive Positioning** (collapsed)
5. **Strategic Implications** (collapsed)
6. **Key Unknowns** (5-7 questions)
7. **Methodology** (collapsed)
8. **Sources** (organized by category)

## Success Criteria

After running, you should have:
- ✅ Intelligence report saved locally
- ✅ 4-5 agent summaries with sourced findings
- ✅ 20-50 cited sources across categories
- ✅ Clear VIBES/DEETS separation
- ✅ Actionable unknowns for future investigation

## Troubleshooting

**"No Twitter/X data"**:
- Install Rube MCP for direct API access
- Or: Skill will fall back to web search automatically

**"Agents taking too long"**:
- Reduce max_results in Twitter search
- Remove Enterprise Testimonial agent
- Use Haiku model for agents instead of Sonnet

**"Report missing sections"**:
- Verify agents completed successfully
- Check agent output files in `/tmp/claude-*/tasks/`
- Re-run with increased timeout if agents timed out

## Support

For complete installation instructions, see: `model-intel-setup-guide.md`

For methodology details, see: `frameworks/intelligence/day-one-model-intelligence-methodology.md` (if available in your vault)

---

**Version**: 1.0 (2026-02-06)
**Tested with**: Claude Code 2.1.32, Sonnet 4.5
**Example run cost**: ~$0.50-1.50 with Rube MCP, ~$0.20-0.50 with built-in tools
