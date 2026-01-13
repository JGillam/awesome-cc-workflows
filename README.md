# Awesome Claude Code Workflows

A curated marketplace of Claude Code plugins, workflows, and configurations to enhance your AI-assisted development experience.

## About

This marketplace provides a collection of reusable Claude Code plugins organized by functional area. Each plugin is self-contained with its own commands, documentation, and installation instructions.

## Quick Start

Register this marketplace in Claude Code to make all plugins available. See the [Claude Code documentation](https://code.claude.com/docs/en/plugins) for details on registering marketplaces.

## Available Plugins

### Session Management

**[jg-session](plugins/jg-session/)** - Maintain context and continuity between Claude Code sessions

A pair of slash commands (`/tidyup` and `/tidydown`) that automate end-of-session cleanup and start-of-session context loading. Creates structured session summaries so you never have to re-explain your work when you return.

- **Commands**: `tidyup`, `tidydown`
- **Version**: 1.0.0
- **Category**: Workflow & Productivity

## Plugin Structure

Each plugin in this marketplace follows a consistent structure:

```
plugins/
└── plugin-name/
    ├── .claude-plugin/
    │   └── plugin.json          # Plugin metadata
    ├── commands/
    │   ├── command1.md           # Command definitions
    │   └── command2.md
    └── README.md                 # Plugin documentation
```

## Installation

Register this marketplace in Claude Code to install plugins. Once registered, all plugins become available directly within Claude Code.

For detailed installation instructions, see the [Claude Code Plugin Documentation](https://code.claude.com/docs/en/plugins).

## Categories

Plugins are organized into categories for easy discovery:

- **Workflow & Productivity**: Tools to enhance development workflows
- **Context Management**: Tools for managing and preserving development context

## Plugin Development

### Creating a Plugin

Want to contribute your own plugin? Follow this structure:

1. Create a directory under `plugins/` with a descriptive name (consider using a namespace prefix like `yourname-pluginname`)
2. Add `.claude-plugin/plugin.json` with metadata
3. Create `commands/` directory with command definition files (`.md`)
4. Write a comprehensive `README.md`
5. Update `.claude-plugin/marketplace.json` to register your plugin

### Plugin Naming Convention

Use a namespace prefix to avoid conflicts:
- `jg-session` (Jason G.'s session management plugin)
- `yourname-yourplugin` (your plugin)

This is similar to scoped packages in npm (`@username/package`) or Java package namespacing (`com.company.product`).

### Plugin Metadata

See existing plugins for examples of `plugin.json` structure. Key fields:
- **id**: Unique identifier (must match directory name)
- **name**: Display name
- **version**: Semantic versioning (major.minor.patch)
- **commands**: Array of command definitions with metadata
- **keywords**: For searchability

## Contributing

Contributions are welcome! This marketplace grows organically as the community develops new tools and workflows.

### How to Contribute

1. Fork this repository
2. Create a new plugin following the structure above
3. Test your commands thoroughly
4. Submit a pull request with:
   - Your plugin directory
   - Updated marketplace.json
   - Clear documentation

### Contribution Guidelines

- **Self-contained**: Each plugin should be independent
- **Well-documented**: Include comprehensive README and examples
- **Tested**: Verify commands work as expected
- **Namespaced**: Use a personal namespace prefix
- **Licensed**: Compatible with CC BY 4.0

## Resources

- [Claude Code Documentation](https://code.claude.com/docs/en/sub-agents)
- [Custom Slash Commands Guide](https://code.claude.com/docs/en/slash-commands)
- [Marketplace Metadata Reference](.claude-plugin/marketplace.json)

## License

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png

Individual plugins may have additional attribution requirements. See each plugin's README for details.
