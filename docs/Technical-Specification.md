# AnA - AI News Agent - Technical Specification v1.0

## System Overview

AnA is an AI-powered news aggregation and research workflow that finds AI news, researches selected topics, and generates content packaging (hooks, titles, descriptions) for video production. The system operates locally with file-based inputs/outputs and supports integration with Obsidian.

**Target User:** Solo content creator producing weekly AI news segments
**Primary Use Case:** Reduce 4-5 hours of manual research to 60-90 minutes of AI-assisted workflow
**Execution Environment:** Google Antigravity desktop (local agents with web search capabilities)

---

## Architecture

### High-Level Flow

```
Input Files → Aggregation → Human Selection → Research → Creative Outputs → Archive
     ↓            ↓              ↓               ↓              ↓             ↓
preferred    categorized    selected-items   research-doc   creative-     markup-
sources.json    news.md         .md             .md         outputs.md   archive.md
```

### Core Principles

1. **Local-first:** All files stored locally, no cloud dependencies beyond API calls
2. **Human-in-loop:** Explicit checkpoints for selection and approval
3. **Incremental:** Each workflow step produces artifact before proceeding
4. **Stateful:** Archive prevents duplicate coverage across runs
5. **Transparent:** All agent outputs visible as markdown files

---

[Full content from /mnt/project/AnA_-_Technical_Specification.md]
