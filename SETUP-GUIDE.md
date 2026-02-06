---
type: system-guide
category: skills
title: "/model-intel Skill - Installation & Setup Guide"
description: "Complete setup instructions for installing and configuring the /model-intel skill for day-one AI model intelligence gathering"
date_created: 2026-02-06
tags:
  - skills
  - setup
  - model-intelligence
  - competitive-intelligence
related:
  - "[[model-intel]]"
---

# /model-intel Skill - Setup Guide

Complete instructions for installing the `/model-intel` skill in your own Claude Code environment to conduct comprehensive day-one intelligence gathering on newly released AI models.

---

## What This Skill Does

Launches 4-5 parallel research agents to capture real-time reactions to new AI model releases within 8 hours of launch. Produces a structured intelligence report with:
- **VIBES**: Social media reactions (Twitter/X, Reddit, HN)
- **DEETS**: Technical benchmarks, enterprise validation, production metrics
- **Competitive positioning** and strategic implications
- **Key unknowns** for future investigation

**Example output**: See the [Claude Opus 4.6 Launch Intelligence Report](https://www.notion.so/descript/Claude-Opus-4-6-Launch-Intelligence-Feb-5-2026-2feabe2e1a508193a1d4cb8aff3754d5)

---

## Prerequisites

### Required
- **Claude Code** (any version with Task tool support)
- **Internet connection** for web research

### Recommended (but not required)
- **Rube MCP** for Twitter/X search and web scraping
- **Notion MCP** if you want to publish reports to Notion
- **Memory MCP** for session context storage

---

## Installation

### Step 1: Install the Skill File

1. Create the skill directory if it doesn't exist:
   ```bash
   mkdir -p ~/.claude/skills/model-intel
   ```

2. Download or create the skill file at `~/.claude/skills/model-intel/SKILL.md`

3. Copy the skill content from the source file (see below)

### Step 2: Install Dependencies

#### Option A: Full Setup (Recommended)

**Install Rube MCP** for Twitter/X search and enhanced web scraping:

1. Add to your `~/.claude/mcp.json`:
   ```json
   {
     "mcpServers": {
       "rube": {
         "command": "npx",
         "args": ["-y", "@composiohq/mcp-server-rube"]
       }
     }
   }
   ```

2. Authenticate Rube (one-time setup):
   - The skill will guide you through authentication on first use
   - You'll need a Composio account (free tier available)
   - Connect Twitter/X integration for TWITTER_RECENT_SEARCH

**Install Notion MCP** (optional - for publishing reports to Notion):

Add to `~/.claude/mcp.json`:
```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "your-notion-api-key"
      }
    }
  }
}
```

Get your Notion API key: https://www.notion.so/my-integrations

#### Option B: Minimal Setup (Built-in Tools Only)

If you don't want to install MCPs, the skill can fall back to built-in tools:
- **WebSearch** replaces TWITTER_RECENT_SEARCH (less comprehensive)
- **WebFetch** replaces Firecrawl scraping
- **Local markdown files** replace Notion publishing

**No additional installation needed** - the skill will work with Claude Code's built-in tools.

### Step 3: Configure the Research Agent

The skill uses the `research-orchestration-agent` to spawn parallel research agents. Verify this agent type is available:

```bash
# Check available agent types
claude ask "What agent types are available via the Task tool?"
```

If `research-orchestration-agent` is not available, you can use `general-purpose` agent instead. Edit the skill file and replace all instances of:
- `subagent_type: research-orchestration-agent`
- with: `subagent_type: general-purpose`

---

## Configuration Options

### Customize Output Location

By default, reports are saved to `intel/competitive/[model-name-slug]-launch-intelligence-[YYYY-MM-DD].md`

To change the output directory, edit line 12 of the skill file:
```markdown
**Output**: Single consolidated intelligence report at `YOUR-DIRECTORY/[model-name-slug]-launch-intelligence-[YYYY-MM-DD].md`
```

### Adjust Research Depth

The skill launches 5 parallel agents. To reduce cost/time:
- Remove the "Enterprise Testimonial Agent" (least critical for initial pulse)
- Reduce `max_results: 100` to `max_results: 50` in Twitter agent parameters

To increase depth:
- Add a 6th agent for LinkedIn reactions
- Add podcast/audio coverage agent
- Increase Twitter max_results to 200

---

## Usage

### Basic Usage

```bash
claude "/model-intel GPT-5 Pro"
claude "/model-intel Gemini Ultra 3.5"
claude "/model-intel Sora 2.0"
```

The skill accepts any model name as an argument.

### Multi-Pass Updates

For afternoon updates to morning reports:
```bash
claude "/model-intel ok now i am looking for an updated look at the reactions and commentary around the [model name] release from this morning. here is the morning report [URL]"
```

The skill will:
1. Fetch the existing report
2. Launch afternoon research agents
3. Add "Afternoon Pulse Check" sections
4. Update key unknowns

---

## Dependency Alternatives

### If You Don't Have Rube MCP

**Twitter/X Search**:
- Replace: `TWITTER_RECENT_SEARCH via Rube MCP`
- With: `WebSearch with query "site:twitter.com [model name]"`
- Trade-off: Less structured data, no engagement metrics, lower quality

**Web Scraping**:
- Replace: `firecrawl_scrape via Rube`
- With: `WebFetch` (built-in)
- Trade-off: Some sites may block, JavaScript rendering issues

### If You Don't Have Notion MCP

**Report Publishing**:
- Replace: Update Notion page
- With: Save markdown file locally, copy/paste to Notion manually
- Trade-off: No automated updates, manual sync required

### If You Don't Have Memory MCP

**Session Storage**:
- Remove the `memory_ingest` calls at the end
- Trade-off: No persistent context across sessions

---

## Testing Your Setup

### Quick Test

Run this command to verify the skill loads:
```bash
claude "/model-intel test"
```

Claude should respond with the research protocol and start spawning agents.

### Full Test

Test with a recent model release:
```bash
claude "/model-intel Claude Opus 4.6"
```

Expected behavior:
1. Claude spawns 4-5 parallel research agents
2. Agents run in background (~3-5 minutes)
3. Final report saved to `intel/competitive/` directory
4. Report includes VIBES, DEETS, sources, unknowns

### Troubleshooting

**"Research agent not found"**:
- Check that `research-orchestration-agent` or `general-purpose` is available
- See Configuration Options above

**"Rube MCP connection failed"**:
- Verify MCP server is running: `claude mcp list`
- Check authentication: skill will prompt for auth on first use
- Fallback: Use built-in WebSearch/WebFetch (see Dependency Alternatives)

**"Twitter search returns empty"**:
- Verify Twitter integration is connected in Rube
- Check Composio account has Twitter/X enabled
- Fallback: Use WebSearch for Twitter coverage

---

## Advanced: Customization

### Add Custom Research Agents

Add a 6th agent for specialized coverage. Edit the skill file and add:

```markdown
6. **LinkedIn Professional Agent**
   - Focus: Enterprise professional reactions, thought leadership posts
   - Tool: Use LinkedIn search via Rube MCP
   - Capture: Industry expert takes, corporate announcements
```

Then add the agent spawn in the research protocol section.

### Custom Output Format

The skill uses a "VIBES + DEETS" structure. To change:

1. Edit the "Output Structure" section (lines 77-204)
2. Modify section headers and content requirements
3. Update the editorial standards accordingly

### Integration with Other Tools

**Export to Linear/GitHub Issues**:
Add to the skill's conclusion:
```markdown
After saving report, create GitHub issue with key unknowns for follow-up research.
```

**Slack Notifications**:
Add notification step:
```markdown
Post report summary to #competitive-intel Slack channel with link to full report.
```

---

## Maintenance

### Keep Dependencies Updated

```bash
# Update Rube MCP
npx @composiohq/mcp-server-rube@latest

# Update Notion MCP
npx @modelcontextprotocol/server-notion@latest
```

### Monitor Usage Costs

The skill spawns 4-5 background agents that can consume significant tokens. Approximate costs per run:
- **With Rube MCP**: ~$0.50-1.50 depending on model chosen for agents
- **With built-in tools only**: ~$0.20-0.50

To reduce costs:
- Use fewer agents (remove Enterprise agent)
- Use Haiku model for research agents instead of Sonnet
- Reduce max_results in Twitter searches

---

## Example Workflow

**Day of model launch** (within 8 hours):

1. Run initial pulse:
   ```bash
   claude "/model-intel Gemini Pro 3.0"
   ```

2. Review generated report in `intel/competitive/`

3. Share with team via Notion (manual copy or via Notion MCP)

**12-16 hours later** (afternoon update):

1. Run afternoon pulse:
   ```bash
   claude "/model-intel afternoon update for Gemini Pro 3.0. morning report: [link]"
   ```

2. Skill updates existing report with new sections

**7-14 days later** (comprehensive review):

1. Run full reassessment when independent benchmarks available
2. Resolve "Key Unknowns" from initial report
3. Archive to `intel/competitive/archive/` if no longer actively tracking

---

## File Structure

After setup, your structure should look like:

```
~/.claude/
├── skills/
│   └── model-intel/
│       ├── SKILL.md (the skill file)
│       └── README.md (this setup guide)
├── mcp.json (MCP server config)
└── settings.json (permissions config)

[your-workspace]/
├── intel/
│   └── competitive/
│       ├── claude-opus-4-6-launch-intelligence-2026-02-05.md
│       ├── gemini-ultra-3-launch-intelligence-2026-xx-xx.md
│       └── archive/
└── frameworks/
    └── intelligence/
        └── day-one-model-intelligence-methodology.md (optional reference)
```

---

## FAQ

**Q: Do I need all the MCP servers?**
A: No. The skill works with built-in WebSearch/WebFetch, but Rube MCP provides significantly better Twitter/X coverage.

**Q: How long does a full research run take?**
A: 3-5 minutes with parallel agents running in background. Afternoon updates are faster (~2-3 min).

**Q: Can I use this for non-AI model launches?**
A: Yes, with modifications. The structure works for any product launch intelligence. Edit the "Scope" line and adjust research sources.

**Q: What if I don't have access to Twitter/X?**
A: The skill will still work, but social sentiment section will rely on web search results mentioning tweets. Quality degrades but still functional.

**Q: Can I schedule this to run automatically?**
A: Not directly, but you could:
1. Use a cron job to trigger Claude Code with the skill
2. Monitor RSS feeds for model announcements
3. Use webhooks to trigger research on launch detection

---

## Credits

This skill was developed for strategic intelligence gathering on AI model launches. The methodology is optimized for Product/Engineering teams conducting evals and Marketing teams tracking narrative.

**Reference implementation**: [Claude Opus 4.6 intelligence report](https://www.notion.so/descript/Claude-Opus-4-6-Launch-Intelligence-Feb-5-2026-2feabe2e1a508193a1d4cb8aff3754d5)

---

## Support

For issues, questions, or contributions:
- Check the troubleshooting section above
- Review the example output to understand expected format
- Verify MCP connections with `claude mcp list`

The skill is designed to be self-contained and work with minimal setup. Start with the minimal configuration and add MCP servers as needed.
