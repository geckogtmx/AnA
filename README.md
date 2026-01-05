# AnA - AI News Agent

**AI-powered news aggregation and research workflow for solo content creators**

AnA reduces 4-5 hours of manual research to 60-90 minutes of AI-assisted workflow. Built for creators producing AI news content.

---

## What It Does

1. **Aggregates** AI news from your preferred sources + manual notes + web search
2. **Categorizes** items automatically (Models, Tools, Papers, Industry, Labs/Orgs)
3. **Deduplicates** against previous coverage
4. **Researches** your selected topics in depth with multi-source verification
5. **Generates** creative outputs (hooks, titles, YouTube descriptions)
6. **Archives** covered topics to prevent repetition

---

## Core Principles

- **Local-first**: All files stored locally, no cloud lock-in
- **Human-in-loop**: You make final decisions on selections and creative outputs
- **Transparent**: All agent outputs visible as markdown files
- **Stateful**: Archive system prevents duplicate coverage
- **Obsidian-ready**: Easy integration with knowledge management tools

---

## Quick Start

### Prerequisites

- [Google Antigravity Desktop](https://antigravity.google/download)
- Google AI Pro account (recommended for better rate limits)

### Setup

1. **Clone and initialize:**
```bash
git clone https://github.com/yourusername/ana-ai-news-agent.git
cd ana-ai-news-agent
```

2. **Create project structure:**
```bash
mkdir -p inputs outputs
```

3. **Configure your sources:**

Edit `inputs/preferred-sources.json`:
```json
[
  {
    "source": "OpenAI Blog",
    "url": "https://openai.com/blog",
    "priority": 1
  },
  {
    "source": "Anthropic News",
    "url": "https://www.anthropic.com/news",
    "priority": 1
  }
]
```

4. **Initialize input files:**

Create `inputs/topics-input.md`:
```markdown
# Manual Topics Input

(Add your notes here throughout the week)
```

Create `inputs/markup-archive.md`:
```markdown
# AI News Archive

## Run History
No previous runs yet.
```

5. **Open in Antigravity:**
   - Launch Antigravity Desktop
   - File > Open Folder > select `ana-ai-news-agent/`
   - Set default model to Gemini 3 Pro (Low) for routine tasks

---

## Workflow

### Step 1: Aggregate News
Run the aggregation agent with your date range (e.g., "last 7 days"):
- Queries all preferred sources
- Reads manual topics from `topics-input.md`
- Supplements with web search if needed
- Auto-categorizes all items
- Flags duplicates against archive

**Output:** `outputs/[date]/aggregated-news.md`

### Step 2: Select Items
Review the categorized list and create `outputs/[date]/selected-items.md`:
```markdown
# Selected Items for Research

## Item 1: Models - Claude 4.5 Release
**Source:** https://anthropic.com/news/...
**Why selected:** Major model update, worth covering
```

### Step 3: Deep Research
Run research agent on selected items:
- Gathers 3+ sources per item
- Verifies claims
- Extracts technical details and context
- Formats into structured document

**Output:** `outputs/[date]/research-doc.md`

### Step 4: Generate Creative Outputs
Run creative agents to generate:
- 5 hook options (15-30 seconds each)
- 3 title variations (question, statement, list formats)
- 1 YouTube description with timestamps and sources

**Output:** `outputs/[date]/creative-outputs.md`

### Step 5: Archive & Reset
- Updates `inputs/markup-archive.md` with covered topics
- Clears `inputs/topics-input.md` for next run
- Logs feedback data for future optimization

---

## File Structure

```
ana-ai-news-agent/
├── inputs/
│   ├── preferred-sources.json    # Your curated sources (max 10)
│   ├── topics-input.md           # Manual notes (cleared each run)
│   └── markup-archive.md         # History of covered topics
│
├── outputs/
│   └── [YYYY-MM-DD]/             # One folder per run
│       ├── aggregated-news.md    # Categorized news list
│       ├── selected-items.md     # Your selections
│       ├── research-doc.md       # Deep research
│       └── creative-outputs.md   # Hooks/titles/description
│
├── docs/
│   ├── Technical-Specification.md
│   ├── DOE-Structure.md
│   ├── Full-Build-Roadmap.md
│   └── Session-Guides/
│       ├── Session-1.md          # Setup & Aggregation
│       ├── Session-2.md          # Research & Creative
│       └── Session-3.md          # Archive & Testing
│
└── README.md
```

---

## Categories

Every news item gets one primary category:

- **Models**: LLM releases, benchmarks, model updates
- **Tools**: APIs, applications, integrations, developer tools
- **Papers**: Research publications, technical reports, arxiv
- **Industry**: Funding, acquisitions, partnerships, regulations
- **Labs/Orgs**: Company announcements, strategy updates (default)

Categories are auto-assigned but can be overridden during selection.

---

## Model Selection Strategy

AnA uses multiple models strategically:

- **Gemini 3 Pro (Low)**: File operations, web search, formatting (fast, quota-friendly)
- **Gemini 3 Pro (High)**: Categorization, reasoning tasks (worth the extra quota)
- **Claude Sonnet 4.5**: Deep research, creative outputs (when depth matters)

With Google AI Pro, you get better rate limits. Use Low mode by default, escalate strategically.

---

## Time Estimates

**Initial Setup:** ~30 minutes  
**Per Run (after setup):** 60-90 minutes
  - Aggregation: 10-15 min
  - Selection: 10-15 min
  - Research: 20-30 min
  - Creative: 15-20 min
  - Archive: 5-10 min

**Goal:** Reduce 4-5 hours of manual work to 60-90 minutes AI-assisted.

---

## Documentation

- **[Technical Specification](docs/Technical-Specification.md)**: Complete module specs and architecture
- **[DOE Structure](docs/DOE-Structure.md)**: Directive, Orchestration, Execution layers
- **[Full Build Roadmap](docs/Full-Build-Roadmap.md)**: 3-session build guide (12 hours total)
- **Session Guides**: Step-by-step instructions with time estimates

---

## Obsidian Integration

AnA outputs are markdown-first for easy Obsidian integration:

**Option 1:** Symlink the outputs folder
```bash
ln -s /path/to/ana-ai-news-agent/outputs /path/to/obsidian-vault/AnA-Outputs
```

**Option 2:** Move entire project into vault
```bash
mv ana-ai-news-agent /path/to/obsidian-vault/
```

**Option 3:** Create agent to copy files
Agent can automatically copy completed runs to your vault location.

---

## Future Enhancements

Not in v1.0, but planned:

- Parallel research (faster processing)
- Trend detection (same story, multiple sources)
- Feedback-driven ranking (learns your preferences)
- Smart category suggestions (based on your overrides)
- Cross-category relationship mapping

---

## Contributing

This is a personal workflow tool, but contributions welcome:

1. Fork the repo
2. Create feature branch (`git checkout -b feature/improvement`)
3. Test thoroughly with your own workflow
4. Submit PR with clear description

---

## License

MIT License - See LICENSE file

---

## Credits

**Built by:** Eduardo García-Torres Resano  
**Project:** Department of One  
**Purpose:** Empower solo creators to build AI-assisted workflows

Part of the [Department of One](https://github.com/yourusername/department-of-one) ecosystem.

---

## Support

Issues and questions: [GitHub Issues](https://github.com/yourusername/ana-ai-news-agent/issues)

For detailed build instructions, see the Session Guides in `/docs/Session-Guides/`

---

**AnA v1.0** | Built with Google Antigravity | Designed for solo creators
