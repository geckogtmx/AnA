# AnA Project Context for Claude

## Project Overview

**AnA (AI News Agent)** is an AI-powered news aggregation and research workflow system designed for solo content creators producing AI news content. It reduces 4-5 hours of manual research to 60-90 minutes of AI-assisted workflow.

## Core Architecture

### Design Principles
- **Local-first**: All files stored locally, no cloud lock-in
- **Human-in-loop**: User makes final decisions on selections and creative outputs
- **Transparent**: All agent outputs visible as markdown files
- **Stateful**: Archive system prevents duplicate coverage
- **Obsidian-ready**: Easy integration with knowledge management tools

### Primary Platform
- Built for **Google Antigravity Desktop**
- Designed to work with multiple AI models (Gemini 3 Pro, Claude Sonnet 4.5)
- All interactions happen through Antigravity's agent interface

## Directory Structure

```
AnA/
├── inputs/
│   ├── preferred-sources.json    # Curated news sources (max 10)
│   ├── topics-input.md           # Manual notes (cleared each run)
│   └── markup-archive.md         # History of covered topics
│
├── outputs/
│   └── [YYYY-MM-DD]/             # One folder per run
│       ├── aggregated-news.md    # Categorized news list
│       ├── selected-items.md     # User selections
│       ├── research-doc.md       # Deep research
│       └── creative-outputs.md   # Hooks/titles/description
│
├── docs/
│   ├── Technical-Specification.md
│   ├── DOE-Structure.md
│   ├── Full-Build-Roadmap.md
│   └── Session-Guides/
│
└── examples/                     # Sample outputs and templates
```

## Key Workflows

### 1. Aggregation
- Queries preferred sources
- Reads manual topics from `topics-input.md`
- Auto-categorizes items (Models, Tools, Papers, Industry, Labs/Orgs)
- Flags duplicates against archive
- Outputs to `outputs/[date]/aggregated-news.md`

### 2. Selection
- User reviews aggregated news
- Creates `selected-items.md` with items for deep research

### 3. Research
- Multi-source verification (3+ sources per item)
- Extracts technical details and context
- Outputs to `research-doc.md`

### 4. Creative Generation
- 5 hook options (15-30 seconds each)
- 3 title variations
- YouTube description with timestamps
- Outputs to `creative-outputs.md`

### 5. Archive
- Updates `markup-archive.md` with covered topics
- Clears `topics-input.md` for next run

## Categories

Every news item gets one primary category:
- **Models**: LLM releases, benchmarks, model updates
- **Tools**: APIs, applications, integrations, developer tools
- **Papers**: Research publications, technical reports, arxiv
- **Industry**: Funding, acquisitions, partnerships, regulations
- **Labs/Orgs**: Company announcements, strategy updates (default)

## File Conventions

### Input Files
- `preferred-sources.json`: JSON array with source, url, priority fields
- `topics-input.md`: Freeform markdown for manual notes
- `markup-archive.md`: Structured markdown with run history

### Output Files
- All outputs are markdown
- Date-based folders: `YYYY-MM-DD` format
- Structured sections with clear headings
- Source citations included

## Model Selection Strategy

Different models for different tasks:
- **Gemini 3 Pro (Low)**: File operations, web search, formatting
- **Gemini 3 Pro (High)**: Categorization, reasoning tasks
- **Claude Sonnet 4.5**: Deep research, creative outputs

## Development Context

### Current Status
- Project in initial setup/build phase
- Documentation-heavy (comprehensive specs in `/docs`)
- No code implementation yet - this is a workflow/agent system
- Built using Antigravity's agent framework (no traditional codebase)

### Build Roadmap
Divided into 3 sessions (see `/docs/Full-Build-Roadmap.md`):
1. Setup & Aggregation
2. Research & Creative
3. Archive & Testing

### Important Files to Reference
- **Technical-Specification.md**: Complete module specs
- **DOE-Structure.md**: Directive, Orchestration, Execution layers
- **Session Guides**: Step-by-step implementation instructions

## When Working with This Project

### Always Consider
1. **Local-first design**: Don't suggest cloud dependencies
2. **Human-in-loop**: User must approve selections/outputs
3. **Markdown outputs**: All outputs must be readable markdown files
4. **Archive awareness**: Check against `markup-archive.md` for duplicates
5. **Obsidian compatibility**: Outputs should work in Obsidian

### Common Tasks
- Creating/updating agent prompts for Antigravity
- Designing markdown templates for outputs
- Improving categorization logic
- Enhancing deduplication algorithms
- Optimizing research source selection

### Avoid
- Suggesting cloud-only solutions
- Removing human decision points
- Breaking markdown compatibility
- Over-automating without user control
- Complex dependencies (keep it simple)

## Target User

Solo content creator producing AI news videos/content who:
- Spends 4-5 hours per week on research
- Wants to reduce to 60-90 minutes
- Values transparency and control
- May use Obsidian for knowledge management
- Prefers local files over cloud services

## Credits

**Built by:** Eduardo García-Torres Resano
**License:** MIT
**Version:** 1.0 (in development)
