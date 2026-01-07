# Session Management with tidyup and tidydown

A pair of slash commands that maintain context between Claude Code sessions through automatic session documentation.

## Overview

These commands work together to create seamless continuity in your development workflow:

- **tidyup** runs at the end of a session to commit your work and create a structured session summary
- **tidydown** runs at the start of the next session to load the previous context

This eliminates the need to manually explain what you were working on when starting a new session.

## The Commands

### /tidyup

End-of-session cleanup that:
- Ensures `.CLAUDE_LAST_SESSION.md` is in `.gitignore`
- Updates project status documentation
- Commits your code
- Creates a new session summary with:
  - What was accomplished (features, bugs fixed, refactoring)
  - Current state (what's working, what's incomplete)
  - Next steps (prioritized actions)
  - Open questions/decisions (blockers, unresolved issues)

**Command Definition:**
```markdown
We are at a good stopping point for this session. Perform the following tidy-up:

1. Ensure .CLAUDE\_LAST\_SESSION.md is in .gitignore (check and add if missing)
2. Update any appropriate status documentation that exists for this project. If we don't have a dedicated file, then you can update @CLAUDE.md, if that's appropriate.
3. Commit our code
4. If a session summary file (.CLAUDE\_LAST\_SESSION.md) exists already, then remove it.
5. Create a new session summary in .CLAUDE\_LAST\_SESSION.md (in the project root) with the following sections:

   * Session Summary header with today's date
   * What was accomplished (features added, bugs fixed, refactoring done, files changed)
   * Current state (what's working, what's incomplete or in-progress, known issues)
   * Next steps (prioritized actions for the next session)
   * Open questions/decisions (unresolved technical decisions, blockers, questions needing user input)

5. Let the user know the session summary has been saved and they can use /tidydown in their next session to load this context
```

### /tidydown

Start-of-session context loader that:
- Reads `.CLAUDE_LAST_SESSION.md` from your project root
- Uses it as context for the current session
- Informs you if no previous session exists (starting fresh)

**Command Definition:**
```markdown
Read the session summary from .CLAUDE_LAST_SESSION.md and use it as context for this session.

If the file doesn't exist, inform the user (they may be starting fresh) and proceed with their request.

After loading the context, help the user with their request. They may have provided additional instructions after this command, or they may follow up with a question about what to work on next.
```

## Installation

These are global slash commands that work across all your projects.

1. Create the slash command files in your global Claude Code commands directory:
   - Windows: `C:\Users\<YourName>\.claude\commands\tidyup.md`
   - macOS/Linux: `~/.claude/commands/tidyup.md`

2. Save each command definition (above) to its respective file

See the [Claude Code documentation](https://code.claude.com/docs/en/slash-commands#custom-slash-commands) for more details on installing global commands.