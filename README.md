# /model-intel - AI Model Launch Intelligence Skill for Claude Code

Day-one intelligence gathering for newly released AI models (LLMs, generative media). Produces comprehensive VIBES + DEETS reports within hours of launch.

[![Example Output](https://img.shields.io/badge/Example-Opus%204.6%20Report-blue)](examples/example-output-opus-4.6.md)

## What This Does

Launch 4-5 parallel research agents to capture real-time reactions to new AI model releases:
- 🐦 **Twitter/X sentiment** with engagement metrics
- 💬 **Community reactions** (HN, Reddit, forums)
- 📊 **Technical benchmarks** (independent validation)
- 🏢 **Enterprise testimonials** and production metrics
- 🎯 **Competitive positioning** analysis
- ❓ **Key unknowns** for future investigation

**Time to first report**: 3-5 minutes after running the command.

## Quick Start

### 1. Install

Paste both lines into Claude Code:

```
/plugin marketplace add elrolio/skills
/plugin install model-intel@elrolio
```

Or drop the skill in by hand:

```bash
git clone https://github.com/elrolio/model-intel-skill.git /tmp/mis
cp -R /tmp/mis/skills/model-intel ~/.claude/skills/
```

### 2. Run
```bash
claude "/model-intel GPT-5 Pro"
```

### 3. Get Your Report
Output saved to: `intel/competitive/[model-name-slug]-launch-intelligence-[date].md`

## Example Output

See real intelligence report from Claude Opus 4.6 launch: [examples/example-output-opus-4.6.md](examples/example-output-opus-4.6.md)

Includes:
- Morning pulse (1-3 hrs post-launch)
- Afternoon pulse (8-16 hrs post-launch)
- Complete VIBES + DEETS analysis
- 50+ cited sources

## Installation Tiers

| Tier | Setup Time | Quality | Cost/Run | Dependencies |
|------|------------|---------|----------|--------------|
| **Minimal** | 5 min | 60% | $0.20-0.50 | Built-in tools only |
| **Recommended** | 15 min | 95% | $0.50-1.50 | + Rube MCP (Twitter API) |
| **Full Stack** | 30 min | 100% | $0.50-1.50 | + Notion + Memory MCP |

**Start with Recommended** for best results.

## Documentation

- **[INDEX.md](INDEX.md)** - Start here (navigation)
- **[INSTALL.md](INSTALL.md)** - Fastest setup path
- **[SETUP-GUIDE.md](SETUP-GUIDE.md)** - Complete instructions
- **[DEPENDENCIES.md](DEPENDENCIES.md)** - Tier comparison
- **[README.md](README.md)** - Skill usage reference

## Requirements

- Claude Code (any recent version)
- Internet connection
- *Recommended*: Rube MCP for Twitter API access ([setup](DEPENDENCIES.md))
- *Optional*: Notion MCP for publishing, Memory MCP for context

## Usage Examples

```bash
# Initial morning pulse (within 8 hrs of launch)
claude "/model-intel Claude Opus 4.6"

# Afternoon update (12-16 hrs later)
claude "/model-intel afternoon update for Claude Opus 4.6. morning report: [URL]"

# Test your setup
claude "/model-intel test"
```

## What You Get

**VIBES** (Social Sentiment):
- What people are hyped about (themes by frequency)
- What people are concerned about (with attribution)
- Community pulse (HN, Reddit, forums)

**DEETS** (Technical Analysis):
- Verified performance strengths (benchmarks)
- Critical technical limitations
- Enterprise validation (real production metrics)
- Breaking changes and migration notes

**Plus**: Competitive positioning, strategic implications, key unknowns, full sources.

## Example Report Structure

```markdown
# Claude Opus 4.6 Launch Intelligence (Feb 5, 2026)

## Executive Summary
[3 paragraphs: standout capabilities, major concerns, positioning]

## THE VIBES
- What People Are Hyped About
- What People Are Concerned About
- Community Forums

## THE DEETS
- Technical Specifications (table)
- Benchmarks Performance (table)
- Enterprise Validation (table)
- Breaking Changes

## Competitive Positioning
[vs GPT-5, vs Gemini, vs Open Source]

## Key Unknowns
[5-7 questions for future investigation]

## Sources
[Organized by category: Official, News, Technical, Community, Enterprise]
```

See [complete example](examples/example-output-opus-4.6.md).

## Contributing

Fork this repo and customize for your needs:
- Modify research sources
- Adjust output format
- Add custom agents
- Change report structure

Pull requests welcome for:
- New research sources
- Better dependency instructions
- Alternative MCP integrations
- Output format improvements

## Cost Expectations

**Per intelligence run** (with Rube MCP):
- Research agents: ~$0.50-1.50
- Token consumption: 100K-200K tokens
- Afternoon updates: ~50% of initial run cost

**Composio free tier**: 1,000 API actions/month (plenty for model tracking)

## Version History

- **1.0** (2026-02-06): Initial release
  - 5-agent parallel research protocol
  - VIBES + DEETS output structure
  - Rube MCP integration for Twitter/X
  - Afternoon pulse update support
  - Example output from Opus 4.6 launch

## License

MIT License - feel free to fork, modify, and share.

## Credits

Developed for strategic intelligence gathering on AI model launches. Methodology optimized for Product/Engineering teams conducting evals and Marketing teams tracking narrative.

**Maintained by**: [@elrolio](https://x.com/elrolio)

## Support

- Check [SETUP-GUIDE.md](SETUP-GUIDE.md) for troubleshooting
- Review [example output](examples/example-output-opus-4.6.md) to understand format
- Open an issue for bugs or questions

---

**Ready to install?** → Start with [INSTALL.md](INSTALL.md)
