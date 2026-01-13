# Session Management Plugin (jg-session)

A pair of slash commands that maintain context between Claude Code sessions through automatic session documentation.

## Overview

These commands work together to create seamless continuity in your development workflow:

- **tidyup** runs at the end of a session to commit your work and create a structured session summary
- **tidydown** runs at the start of the next session to load the previous context

This eliminates the need to manually explain what you were working on when starting a new session.

## Commands

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

### /tidydown

Start-of-session context loader that:
- Reads `.CLAUDE_LAST_SESSION.md` from your project root
- Uses it as context for the current session
- Informs you if no previous session exists (starting fresh)

## Installation

This plugin is installed by registering the practical-cc marketplace in Claude Code. Once registered, the tidyup and tidydown commands become available automatically.

For detailed installation instructions, see the [Claude Code Plugin Documentation](https://code.claude.com/docs/en/plugins).

## Usage

### Typical Workflow

**End of session:**
```
/tidyup
```

**Start of next session:**
```
/tidydown
```

Then continue with your work. Claude will have full context of what you were doing.

### Example

```
User: /tidyup
Claude: I've completed the session tidy-up:
1. Verified .CLAUDE_LAST_SESSION.md is in .gitignore
2. Committed changes: "Implement user authentication feature"
3. Created session summary with accomplishments and next steps

The session summary has been saved to .CLAUDE_LAST_SESSION.md
Use /tidydown in your next session to load this context.

[Next session]
User: /tidydown
Claude: I've loaded the session context. I can see we implemented user authentication
and were planning to add password reset functionality next. How would you like to proceed?
```

## How It Works

### Session Summary Structure

The tidyup command creates a markdown file (`.CLAUDE_LAST_SESSION.md`) with:

- **Session Summary**: Date and high-level overview
- **What was accomplished**: Features, fixes, refactoring performed
- **Current state**: What's working, incomplete work, known issues
- **Next steps**: Prioritized list of upcoming work
- **Open questions**: Blockers, decisions needed, questions for you

### Git Integration

The tidyup command integrates with your git workflow:
- Automatically commits changes before creating the session summary
- Ensures the session file is gitignored (not committed to the repository)
- Maintains clean commit history

## Best Practices

1. **Use tidyup before long breaks**: Before stepping away for more than an hour or ending your day
2. **Always tidydown when returning**: Start each session with /tidydown to load context
3. **Review the summary**: After tidyup, review the .CLAUDE_LAST_SESSION.md to ensure accuracy
4. **Update CLAUDE.md**: tidyup will update project-level documentation when appropriate

## Troubleshooting

**Issue**: `/tidyup` or `/tidydown` not recognized

**Solution**: Ensure the practical-cc marketplace is registered in Claude Code and the plugin is enabled

**Issue**: Session summary not found

**Solution**: You may not have run `/tidyup` in the previous session. This is normal for new projects.

**Issue**: Git commit fails during tidyup

**Solution**: Ensure you have changes to commit and proper git configuration (user.name, user.email)

## Version History

### 1.0.0
- Initial release
- tidyup command for end-of-session cleanup
- tidydown command for start-of-session context loading

## License

This plugin is licensed under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author

Created by Jason G. as part of the [practical-cc](https://github.com/jasongilman/practical-cc) marketplace.
