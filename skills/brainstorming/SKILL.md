---
name: brainstorming
description: "MUST use before building features, creating components, adding functionality, or designing new behavior. Use when user says 'build', 'create', 'add feature', 'implement', 'design', or describes something new to build. Explores requirements through questions before writing code."
---

# Brainstorming Ideas Into Designs

## Overview

Help turn ideas into fully formed designs and specs through natural collaborative dialogue.

Start by understanding the current project context, then ask questions one at a time to refine the idea. Once you understand what you're building, present the design in small sections (200-300 words), checking after each section whether it looks right so far.

## The Process

**Understanding the idea:**
- Check out the current project state first (files, docs, recent commits)
- Ask questions one at a time to refine the idea
- Prefer multiple choice questions when possible, but open-ended is fine too
- Only one question per message - if a topic needs more exploration, break it into multiple questions
- Focus on understanding: purpose, constraints, success criteria

**Exploring approaches:**
- Propose 2-3 different approaches with trade-offs
- Present options conversationally with your recommendation and reasoning
- Lead with your recommended option and explain why

**Presenting the design:**
- Once you believe you understand what you're building, present the design
- Break it into sections of 200-300 words
- Ask after each section whether it looks right so far
- Cover: architecture, components, data flow, error handling, testing
- Be ready to go back and clarify if something doesn't make sense

## Stack-Specific Decision Trees

When brainstorming features for your stack, work through these decision trees:

### Platform Decision

```
Is this feature...
├── iOS/native only?
│   └── Use indie-stack:swift-ios-app patterns
├── Web only?
│   └── Use Next.js + Vercel patterns
├── Backend/API only?
│   └── Use indie-stack:supabase-setup patterns
└── Full stack (mobile + web + backend)?
    └── Design backend first, then platform UIs
```

### Data Architecture

```
Does this feature need data persistence?
├── No → Local state only (SwiftUI @State, React useState)
├── Yes, local only → SwiftData (iOS) or localStorage (web)
├── Yes, synced across devices →
│   ├── Real-time sync needed?
│   │   ├── Yes → Supabase Realtime
│   │   └── No → Supabase REST + manual sync
│   └── Offline support needed?
│       ├── Yes → SwiftData + SyncService pattern
│       └── No → Direct Supabase queries
└── Yes, shared between users →
    └── Supabase with appropriate RLS policies
```

### Authentication Strategy

```
Does this feature need auth?
├── No → Public access
├── Yes, identified user only →
│   ├── New app? → Sign in with Apple (iOS) or magic link (web)
│   ├── Existing app? → Use existing AuthService
│   └── Trial flow? → One free action, then require sign-in
└── Yes, with roles/permissions →
    └── Add roles to profiles table + RLS policies
```

### AI Integration

```
Does this feature use AI?
├── No → Skip this section
├── Yes →
│   ├── Where does AI run?
│   │   ├── Edge Function (Supabase) → indie-stack:edge-function
│   │   └── Client-side → Not recommended (API key exposure)
│   ├── What AI provider?
│   │   ├── Vision/multimodal → Gemini (good price/performance)
│   │   ├── Text generation → Claude or GPT-4
│   │   └── Embeddings → OpenAI text-embedding-3-small
│   └── Structured output needed?
│       ├── Yes → Use JSON mode + Zod validation
│       └── No → Stream response to UI
```

### Offline-First Decision

```
Should this work offline?
├── Core feature that users expect to work anywhere →
│   └── YES: SwiftData local-first, sync when connected
├── Real-time collaborative feature →
│   └── NO: Require connection, show clear offline state
├── Read-heavy feature (viewing history, stats) →
│   └── YES: Cache data locally, refresh when connected
└── Write-heavy feature (creating content) →
    └── YES: Save locally, queue uploads for later
```

## Key Questions to Ask

When brainstorming, make sure to cover:

1. **Platform**: iOS only, web only, or both?
2. **Auth**: Who can use this? Anonymous, authenticated, or specific roles?
3. **Data**: Where does data live? Local, synced, or shared?
4. **Offline**: Should this work without internet?
5. **AI**: Is AI involved? Where should it run?
6. **UX**: What's the happy path? What are the error cases?

## After the Design

**Documentation:**
- Write the validated design to `docs/plans/YYYY-MM-DD-<topic>-design.md`
- Commit the design document to git

**Implementation (if continuing):**
- Ask: "Ready to create the implementation plan?"
- Use indie-stack:writing-plans to create detailed implementation plan
- Use indie-stack:subagent-driven-development to execute

## Key Principles

- **One question at a time** - Don't overwhelm with multiple questions
- **Multiple choice preferred** - Easier to answer than open-ended when possible
- **YAGNI ruthlessly** - Remove unnecessary features from all designs
- **Explore alternatives** - Always propose 2-3 approaches before settling
- **Incremental validation** - Present design in sections, validate each
- **Be flexible** - Go back and clarify when something doesn't make sense
- **Think UX first** - Every feature should have clear user flows
