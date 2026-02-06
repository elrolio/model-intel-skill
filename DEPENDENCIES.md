# /model-intel Skill - Dependency Quick Reference

## Installation Tiers

### Tier 1: Minimal (Works Out of the Box)
**Setup time**: 0 minutes | **Quality**: 60% | **Cost per run**: ~$0.20-0.50

- ✅ Claude Code (built-in Task tool)
- ✅ WebSearch (built-in)
- ✅ WebFetch (built-in)

**What you get**: Basic intelligence reports using web search for all sources.

**What you miss**: Structured Twitter data, engagement metrics, reliable web scraping.

---

### Tier 2: Recommended (Best Quality)
**Setup time**: 10-15 minutes | **Quality**: 95% | **Cost per run**: ~$0.50-1.50

**Add these MCPs**:

#### 1. Rube MCP (Critical for Twitter/X)
```bash
# Install
npm install -g @composiohq/mcp-server-rube

# Add to ~/.claude/mcp.json
{
  "mcpServers": {
    "rube": {
      "command": "npx",
      "args": ["-y", "@composiohq/mcp-server-rube"]
    }
  }
}
```

**Authentication**:
1. Create free Composio account: https://app.composio.dev
2. Connect Twitter/X integration
3. On first use, skill will prompt for auth

**What you get**:
- Direct Twitter API access (not web scraping)
- Engagement metrics (likes, RTs, quotes)
- Author verified status, follower counts
- Structured tweet data

#### 2. research-orchestration-agent
Verify it's available: `claude ask "What agent types are available?"`

If not available, edit skill to use `general-purpose` agent instead.

---

### Tier 3: Full Stack (Publishing + Memory)
**Setup time**: 20-30 minutes | **Quality**: 100% | **Cost per run**: ~$0.50-1.50

**Add these MCPs**:

#### 3. Notion MCP (Optional - for publishing)
```bash
# Install
npm install -g @modelcontextprotocol/server-notion

# Add to ~/.claude/mcp.json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "your-key-here"
      }
    }
  }
}
```

Get API key: https://www.notion.so/my-integrations

**What you get**: Direct publishing to Notion workspace, automated updates.

#### 4. Memory MCP (Optional - for session context)
```bash
# Usually pre-installed with Claude Code
# Verify: claude mcp list | grep memory
```

**What you get**: Persistent context across sessions, conversation history.

---

## Feature Comparison by Tier

| Feature | Minimal | Recommended | Full Stack |
|---------|---------|-------------|------------|
| **Twitter/X Coverage** | Web search mentions | Direct API, engagement metrics | Same as Recommended |
| **Web Scraping** | Basic (WebFetch) | Firecrawl (advanced) | Same as Recommended |
| **HN/Reddit** | Web search | Web search | Same as Recommended |
| **Benchmarks** | Web search | Web search | Same as Recommended |
| **Report Output** | Local markdown | Local markdown | Local + Notion |
| **Session Memory** | None | None | Full context persistence |
| **Setup Time** | 0 min | 10-15 min | 20-30 min |
| **Quality Score** | 60% | 95% | 100% |
| **Cost per Run** | $0.20-0.50 | $0.50-1.50 | $0.50-1.50 |

---

## Which Tier Should You Choose?

**Choose Minimal if**:
- You want to try the skill immediately
- You only need occasional model intelligence
- You don't have time for MCP setup

**Choose Recommended if**:
- You need high-quality social sentiment data
- You want structured Twitter engagement metrics
- You're tracking model launches regularly

**Choose Full Stack if**:
- You publish reports to Notion workspace
- You want session context persistence
- You're running systematic competitive intelligence

---

## Upgrade Path

Start with **Minimal** → test the skill → upgrade to **Recommended** if you need better Twitter data → add **Notion MCP** if you want automated publishing.

Each tier is fully functional. You can always upgrade later without reinstalling the skill.

---

## Installation Commands (Copy-Paste)

### For Recommended Tier

```bash
# 1. Install skill
mkdir -p ~/.claude/skills/model-intel
curl -o ~/.claude/skills/model-intel/SKILL.md [SKILL_FILE_URL]

# 2. Add Rube MCP to config
cat >> ~/.claude/mcp.json << 'EOF'
{
  "mcpServers": {
    "rube": {
      "command": "npx",
      "args": ["-y", "@composiohq/mcp-server-rube"]
    }
  }
}
EOF

# 3. Restart Claude Code
# 4. Run skill - will prompt for Composio auth on first use
claude "/model-intel test"
```

### For Full Stack

```bash
# Same as Recommended, plus:

# 5. Add Notion MCP
# First, get your Notion API key from https://www.notion.so/my-integrations
# Then add to mcp.json:
cat >> ~/.claude/mcp.json << 'EOF'
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "YOUR_KEY_HERE"
      }
    }
  }
}
EOF

# 6. Restart Claude Code
```

---

## Verification Checklist

After installation, verify:

- [ ] Skill loads: `claude "/model-intel test"`
- [ ] Agents spawn successfully (check for 4-5 background tasks)
- [ ] Rube MCP connected: `claude mcp list | grep rube`
- [ ] Twitter search works: Try a quick Twitter/X search via Rube
- [ ] Reports save to expected directory
- [ ] (If Notion) Notion MCP connected: `claude mcp list | grep notion`

---

## Quick Comparison: Built-in vs Rube

**Twitter Coverage Example** (for a model launch):

| Method | Sample Size | Engagement Data | Quality |
|--------|-------------|-----------------|---------|
| **WebSearch** | ~10-20 tweet mentions | No metrics | Low (relies on news sites quoting tweets) |
| **Rube MCP** | 100-200 actual tweets | Likes, RTs, quotes, impressions | High (direct API access) |

**The difference matters** for sentiment analysis and identifying high-signal voices.

---

## Next Steps

1. Choose your tier (start with Recommended)
2. Follow setup instructions in `model-intel-setup-guide.md`
3. Run a test: `claude "/model-intel [recent model]"`
4. Review output quality
5. Upgrade tier if needed

**Estimated setup**: 15 minutes for Recommended tier, 30 minutes for Full Stack.
