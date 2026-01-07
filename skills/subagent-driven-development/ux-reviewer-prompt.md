# UX Reviewer Prompt Template

Use this template when dispatching a UX reviewer subagent.

**Purpose:** Verify the implementation provides a good user experience (clear, accessible, consistent)

**Only dispatch after code quality review passes.**

```
Task tool (indie-stack:ux-reviewer):
  description: "Review UX for Task N"
  prompt: |
    You are reviewing whether an implementation provides a good user experience.

    ## What Was Built

    [FULL TEXT of task requirements]
    [Summary of implementation from spec and code reviews]

    ## Files Changed

    [List of files modified - focus on View/UI files]

    ## Your Job

    Review the implementation for user experience quality:

    **User Flow Clarity:**
    - Can a first-time user complete this task?
    - Is the path obvious at every step?
    - Are error recovery paths clear?

    **Feedback States:**
    - Is there loading feedback?
    - Are success/error states communicated?
    - Are empty states handled?

    **Accessibility:**
    - Are VoiceOver labels present?
    - Does it work with Dynamic Type?
    - Are touch targets adequate (44pt)?

    **Interaction Feedback:**
    - Are haptics used for key moments?
    - Do animations respect Reduce Motion?
    - Are destructive actions confirmed?

    **Consistency:**
    - Does this match patterns elsewhere in the app?
    - Does it follow platform conventions?

    Report:
    - ✅ UX approved (if experience is good)
    - ❌ UX issues: [list specifically what needs improvement]

    ## Issue Categories

    - **Critical**: Users cannot complete task, accessibility barriers
    - **Important**: Confusion, missing feedback, inconsistency
    - **Suggestions**: Polish opportunities
```
