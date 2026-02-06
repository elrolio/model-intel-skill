# /model-intel Skill - Complete Package

**Version**: 1.0
**Release Date**: February 6, 2026
**Tested With**: Claude Code 2.1.32, Sonnet 4.5

---

## What's Included

This package contains everything you need to install and run the `/model-intel` skill for day-one AI model intelligence gathering.

### Files in This Package

```
model-intel-package/
├── INDEX.md                 # ← You are here (start here)
├── SKILL.md                 # Main skill file (install to ~/.claude/skills/model-intel/)
├── README.md                # Quick reference (how to use the skill)
├── INSTALL.md               # One-command installation (fastest setup)
├── SETUP-GUIDE.md           # Complete setup instructions (detailed walkthrough)
├── DEPENDENCIES.md          # Dependency reference (what you need and why)
└── examples/
    └── example-output-opus-4.6.md  # Real output from Opus 4.6 launch
```

---

## Installation Paths (Choose One)

### Path 1: Quick Install (15 minutes)
**Best for**: People who want to start immediately

1. Read: `INSTALL.md`
2. Copy-paste the one-command install script
3. Restart Claude Code
4. Run: `claude "/model-intel test"`

**You get**: Recommended tier (Rube MCP for Twitter, high-quality data)

---

### Path 2: Manual Setup (30 minutes)
**Best for**: People who want to understand each component

1. Read: `SETUP-GUIDE.md` (comprehensive walkthrough)
2. Follow step-by-step instructions
3. Customize as needed
4. Test with example model

**You get**: Full control over configuration, optional features

---

### Path 3: Minimal (5 minutes)
**Best for**: People who just want to try it without dependencies

1. Copy `SKILL.md` to `~/.claude/skills/model-intel/SKILL.md`
2. Run: `claude "/model-intel test"`

**You get**: Basic functionality with built-in tools only (no Twitter API)

---

## What You'll Get

After installation, running `claude "/model-intel GPT-5 Pro"` will:

1. **Spawn 4-5 parallel research agents** to gather intelligence
2. **Search Twitter/X, HN, Reddit, blogs** for reactions
3. **Extract benchmarks, testimonials, concerns** from coverage
4. **Produce structured report** in ~5 minutes

**Example output**: See `examples/example-output-opus-4.6.md`

---

## Installation Flow Chart

```
START
  ↓
Do you have npm/Node.js installed?
  ├─ YES → Go to Quick Install (INSTALL.md)
  │         ↓
  │       Do you want Twitter API access?
  │         ├─ YES → Install Rube MCP (15 min)
  │         └─ NO → Skip to Step 6 (use built-in tools)
  │
  └─ NO → Manual Setup (SETUP-GUIDE.md)
            ↓
          Follow manual installation steps
            ↓
          Optionally add Rube MCP later
```

---

## Quick Reference

### Core Command
```bash
claude "/model-intel [Model Name]"
```

### Examples
```bash
# Initial pulse (within 8 hrs of launch)
claude "/model-intel GPT-5 Pro"

# Afternoon update (12-16 hrs later)
claude "/model-intel afternoon update for GPT-5 Pro. morning report: [link]"

# Test installation
claude "/model-intel test"
```

### Output Location
Reports save to: `intel/competitive/[model-name-slug]-launch-intelligence-[YYYY-MM-DD].md`

(Customize in SKILL.md line 12 if needed)

---

## Dependencies at a Glance

| Component | Required? | Setup Time | Impact |
|-----------|-----------|------------|--------|
| **Claude Code** | ✅ Yes | Already have | Core platform |
| **Task tool** | ✅ Yes | Built-in | Spawns agents |
| **WebSearch/WebFetch** | ✅ Yes | Built-in | Fallback research |
| **Rube MCP** | ⚠️ Recommended | 10 min | +40% quality (Twitter API) |
| **Notion MCP** | ⬜ Optional | 5 min | Auto-publishing |
| **Memory MCP** | ⬜ Optional | 5 min | Session context |

**Bottom line**: Works immediately with built-in tools. Add Rube MCP for best quality.

---

## First-Time Setup Checklist

- [ ] Read this INDEX.md (you're here!)
- [ ] Choose installation path (Quick/Manual/Minimal)
- [ ] Follow instructions in chosen guide
- [ ] Restart Claude Code
- [ ] Run test: `claude "/model-intel test"`
- [ ] Verify agents spawn successfully
- [ ] Check example output matches your expectations
- [ ] (Optional) Install Rube MCP for Twitter access
- [ ] (Optional) Install Notion MCP for publishing
- [ ] Run first real intelligence gathering

**Expected time to first successful run**: 5-30 minutes depending on path.

---

## What's Next

After successful installation:

1. **Review the example output** (`examples/example-output-opus-4.6.md`) to understand the report structure
2. **Customize the skill** if needed (see SETUP-GUIDE.md Advanced section)
3. **Set up notifications** when new models launch
4. **Create your first intelligence report** for a recent model release

---

## Support Materials

- **Quick start**: Start with `README.md`
- **Installation**: Use `INSTALL.md` for fastest setup
- **Detailed guide**: Read `SETUP-GUIDE.md` for complete instructions
- **Dependencies**: Check `DEPENDENCIES.md` for tier comparisons
- **Example**: Review `examples/` directory for expected output format

---

## Skill Philosophy

This skill is designed to be:
- ✅ **Self-contained**: Works with minimal dependencies
- ✅ **Flexible**: Multiple installation tiers (minimal → full)
- ✅ **Fast**: Parallel agents complete in 3-5 minutes
- ✅ **Comprehensive**: VIBES + DEETS structure covers all angles
- ✅ **Shareable**: Standard markdown output, Notion-ready

**Key principle**: Start simple, upgrade as needed.

---

## Sharing This Skill

To share with others:

1. **GitHub**: Create a repo with this package directory
2. **Direct share**: Zip this folder and send
3. **Documentation**: Share the example output first so people see what they get

When sharing, point recipients to:
- `INDEX.md` (start here)
- `examples/` (see what you'll get)
- `INSTALL.md` (quickest path to working skill)

---

## Questions?

- **"Do I need all these files?"** — No. Minimum is just `SKILL.md`. Others are documentation.
- **"Which installation tier should I choose?"** — See DEPENDENCIES.md for comparison.
- **"How much does this cost to run?"** — ~$0.50-1.50 per intelligence run with Rube MCP.
- **"Can I customize the output?"** — Yes. See SETUP-GUIDE.md Advanced section.
- **"What if I don't have Twitter access?"** — Still works, uses web search (lower quality).

---

**Ready to install?** → Start with `INSTALL.md` for fastest setup.

**Want to understand first?** → Read `README.md` then `SETUP-GUIDE.md`.

**Just browsing?** → Check `examples/example-output-opus-4.6.md` to see what you'll get.
