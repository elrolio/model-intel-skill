# /model-intel Skill - One-Command Installation

## Fastest Install (Recommended Tier)

Copy-paste this into your terminal:

```bash
# 1. Create skill directory
mkdir -p ~/.claude/skills/model-intel

# 2. Download skill file (replace with actual URL when shared)
# For now, manually copy the SKILL.md file to ~/.claude/skills/model-intel/

# 3. Add Rube MCP to Claude Code config
# First, backup your current config
cp ~/.claude/mcp.json ~/.claude/mcp.json.backup 2>/dev/null || echo '{"mcpServers": {}}' > ~/.claude/mcp.json

# 4. Install Rube MCP server
npm install -g @composiohq/mcp-server-rube

# 5. Add to config (manual step - paste this into ~/.claude/mcp.json under "mcpServers")
cat << 'EOF'

Add this to your ~/.claude/mcp.json under "mcpServers":

  "rube": {
    "command": "npx",
    "args": ["-y", "@composiohq/mcp-server-rube"]
  }

EOF

# 6. Restart Claude Code
echo "✅ Installation complete. Restart Claude Code and run: claude '/model-intel test'"
```

---

## Manual Installation (Step-by-Step)

### 1. Create Skill Directory
```bash
mkdir -p ~/.claude/skills/model-intel
```

### 2. Copy Skill Files

Download these files to `~/.claude/skills/model-intel/`:
- `SKILL.md` (main skill file - REQUIRED)
- `README.md` (quick reference)
- `model-intel-setup-guide.md` (complete setup instructions)
- `model-intel-dependencies.md` (dependency reference)

### 3. Install Rube MCP

**a. Install the npm package**:
```bash
npm install -g @composiohq/mcp-server-rube
```

**b. Edit `~/.claude/mcp.json`** and add under `"mcpServers"`:
```json
"rube": {
  "command": "npx",
  "args": ["-y", "@composiohq/mcp-server-rube"]
}
```

Your full `mcp.json` should look like:
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

**c. Restart Claude Code**

### 4. Authenticate Rube

On first use, the skill will prompt you to authenticate. Follow these steps:

1. Create free Composio account: https://app.composio.dev
2. Connect Twitter/X integration
3. Claude will provide an authentication URL
4. Complete OAuth flow
5. Return to Claude - authentication persists

### 5. Verify Installation

```bash
# Check MCP is loaded
claude mcp list

# You should see:
# - rube (connected)

# Test the skill
claude "/model-intel test"

# Should spawn 4-5 research agents
```

---

## Minimal Installation (No MCPs)

If you don't want to install any dependencies:

1. Copy only `SKILL.md` to `~/.claude/skills/model-intel/SKILL.md`
2. Edit the skill file and replace:
   - `TWITTER_RECENT_SEARCH via Rube MCP` → `WebSearch with "site:twitter.com"`
   - `firecrawl_scrape` → `WebFetch`
3. Run: `claude "/model-intel [model name]"`

**Trade-off**: Lower quality Twitter data, no engagement metrics, but works immediately.

---

## Troubleshooting

### "Rube MCP not found"
```bash
# Verify installation
npm list -g @composiohq/mcp-server-rube

# Reinstall if needed
npm install -g @composiohq/mcp-server-rube

# Check Claude can see it
claude mcp list
```

### "research-orchestration-agent not found"

Edit `SKILL.md` and replace all instances:
```markdown
# Change this:
subagent_type: research-orchestration-agent

# To this:
subagent_type: general-purpose
```

### "Twitter search returns no results"

1. Check Composio integration: https://app.composio.dev/integrations
2. Verify Twitter/X is connected and active
3. Re-authenticate if needed

### "Skill not appearing in /model-intel"

```bash
# Check skill directory
ls -la ~/.claude/skills/model-intel/

# Should show:
# SKILL.md

# Restart Claude Code
```

---

## Uninstallation

```bash
# Remove skill
rm -rf ~/.claude/skills/model-intel

# Remove Rube MCP from mcp.json (manual edit)

# Uninstall npm package
npm uninstall -g @composiohq/mcp-server-rube

# Restart Claude Code
```

---

## What You'll Need

| Item | Required? | Where to Get |
|------|-----------|--------------|
| Claude Code | ✅ Yes | https://claude.com/code |
| Composio Account | ⚠️ Recommended | https://app.composio.dev (free tier) |
| Twitter/X Account | ⚠️ Recommended | For connecting Twitter integration |
| Notion Account | ⬜ Optional | For publishing reports |
| npm/Node.js | ⚠️ Recommended | For installing MCP servers |

---

## Quick Start After Install

```bash
# 1. Run for a recent model
claude "/model-intel Claude Opus 4.6"

# 2. Wait 3-5 minutes for agents to complete

# 3. Check output
cat intel/competitive/claude-opus-4-6-launch-intelligence-*.md

# 4. For afternoon update
claude "/model-intel afternoon update for Claude Opus 4.6. morning report: [path-to-report]"
```

---

## Cost Expectations

**Per research run**:
- With Rube MCP: ~$0.50-1.50 (depending on agent model choice)
- Built-in tools only: ~$0.20-0.50

**Token consumption**:
- ~100K-200K tokens per run (across 4-5 agents)
- Afternoon updates: ~50K-100K tokens

**Composio free tier**: 1,000 actions/month (plenty for occasional model intelligence)

---

## Support & Updates

For issues or questions:
1. Check the troubleshooting section above
2. Review `model-intel-setup-guide.md` for detailed instructions
3. Verify example output matches expected format

**Skill version**: 1.0 (2026-02-06)
**Tested with**: Claude Code 2.1.32, Sonnet 4.5, Rube MCP v1.x
