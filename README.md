# indie-stack

A specialized Claude Code plugin for indie developers building apps with Swift/SwiftUI, Supabase, Vercel, and AI.

Forked from [superpowers](https://github.com/obra/superpowers) by Jesse Vincent, customized for a specific tech stack with a 3-stage review workflow.

## What's Different from Superpowers

| Feature | Superpowers | indie-stack |
|---------|-------------|-------------|
| **Review Stages** | 2 (spec + code) | 3 (spec + code + UX) |
| **TDD** | Strict "Iron Law" | Flexible, allows prototyping |
| **Stack Focus** | General purpose | Swift, Supabase, Vercel, AI |
| **Reviewers** | Generic code-reviewer | iOS, Backend, and UX specialists |

## Skills (11)

### From Superpowers (Modified)
- **brainstorming** - Collaborative design with stack-specific decision trees
- **writing-plans** - Detailed implementation plans
- **subagent-driven-development** - 3-stage review: spec → code → UX
- **testing-flexible** - Test guidance (encouraged, not blocking)
- **verification-before-completion** - Evidence-based completion
- **systematic-debugging** - 4-phase root cause analysis
- **dispatching-parallel-agents** - Multiple agents for independent issues
- **requesting-code-review** - Code review workflow
- **receiving-code-review** - Handling review feedback

### New Stack-Specific
- **swift-ios-app** - iOS architecture with SwiftUI, SwiftData, Swift 6
- **supabase-setup** - Backend with Auth, RLS, Storage, Edge Functions

## Agents (4)

| Agent | Focus |
|-------|-------|
| **ios-reviewer** | Swift 6 concurrency, SwiftUI patterns, SwiftData, memory management |
| **backend-reviewer** | RLS security, Edge Functions, TypeScript, Supabase client usage |
| **ux-reviewer** | User flows, feedback states, accessibility, consistency |
| **code-reviewer** | General code quality (from superpowers) |

## 3-Stage Review Workflow

```
┌─────────────────────────────────────────────────────────────┐
│                    PER-TASK WORKFLOW                        │
├─────────────────────────────────────────────────────────────┤
│  1. IMPLEMENT      Implementer builds the feature           │
│         ↓                                                   │
│  2. SPEC REVIEW    Does code match requirements?            │
│         ↓                                                   │
│  3. CODE REVIEW    Is code quality good? (iOS or Backend)   │
│         ↓                                                   │
│  4. UX REVIEW      Is user experience good?                 │
│         ↓                                                   │
│  5. COMPLETE       Task marked done                         │
└─────────────────────────────────────────────────────────────┘
```

## Installation

### Claude Code

```bash
# Install from local directory
cd ~/projects/indie-stack
# Claude Code will detect the plugin structure
```

Or reference in your project's settings.

## Tech Stack

This plugin is optimized for:
- **iOS**: Swift 6, SwiftUI, SwiftData, iOS 17+
- **Backend**: Supabase (Auth, Postgres, Storage, Edge Functions)
- **Web**: Next.js, Vercel, TypeScript
- **AI**: Gemini API, Vercel AI SDK
- **Package Manager**: Bun (for TypeScript projects)

## Credits

Based on [superpowers](https://github.com/obra/superpowers) by Jesse Vincent. The core philosophy (systematic workflows, verification before completion, subagent-driven development) comes from superpowers - indie-stack adds stack-specific skills and the UX review stage.

## License

MIT
