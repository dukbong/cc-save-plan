<div align="center">

# 📋 Save Plan Plugin

**A Claude Code plugin for saving auto-generated plan files to your project**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude-Code-5A67D8)](https://claude.ai)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/hyeonsung/cc-save-plan)

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Examples](#-examples) • [Contributing](#-contributing)

</div>

---

## 🎯 Overview

When you use `/plan` in Claude Code, plan files are automatically generated in `~/.claude/plans/`. This plugin makes it easy to copy those plans into your project for version control and documentation purposes.

## ✨ Features

- 💾 **Easy Plan Saving**: Copy plans from global directory to your project with one command
- 🔄 **Version Control**: Track implementation plans alongside your code in git
- 🛡️ **Duplicate Handling**: Smart conflict resolution when files already exist
- 🔧 **Automatic Sanitization**: Handles special characters in filenames automatically
- 📁 **Auto-Organization**: Creates `.claude/plan/` directory structure for you

## 📦 Installation

### From Claude Marketplace (Recommended)

```bash
claude plugin install stash
```

### Manual Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/hyeonsung/cc-save-plan.git
   cd cc-save-plan
   ```

2. Link the plugin:
   ```bash
   claude plugin link .
   ```

## 🚀 Usage

### Basic Command

```bash
/stash:it <plan_name>
```

### How It Works

1. Finds the latest plan file from `~/.claude/plans/`
2. Creates `.claude/plan/` directory in your project (if needed)
3. Copies the plan with your specified name

### Filename Rules

The plugin automatically sanitizes filenames for you:

| Input | Output |
|-------|--------|
| `/stash:it My Plan!` | `My-Plan.md` |
| `/stash:it auth_refactor` | `auth_refactor.md` |
| `/stash:it plan-v2.md` | `plan-v2.md` |

- Valid characters: alphanumeric, hyphens (`-`), underscores (`_`)
- `.md` extension added automatically if not provided
- Special characters are converted to hyphens

### Duplicate File Handling

If a file with the same name already exists, you'll be prompted with three options:

1. **Overwrite**: Replace the existing file completely
2. **Version**: Save as `plan-name-v2.md`, `plan-name-v3.md`, etc.
3. **Cancel**: Exit without making changes

## 📚 Examples

### Example 1: Basic Usage

```bash
/stash:it feature-implementation
```

**Output:**
```
Plan saved successfully to .claude/plan/feature-implementation.md
Full path: /home/user/project/.claude/plan/feature-implementation.md
```

### Example 2: Handling Duplicates

```bash
/stash:it auth-refactor
```

If `auth-refactor.md` already exists, you'll see:
```
A plan file named 'auth-refactor.md' already exists. What would you like to do?
• Overwrite the existing file
• Save with a new version number (e.g., auth-refactor-v2.md)
• Cancel the operation
```

### Example 3: Special Characters

```bash
/stash:it "My New Feature!!"
```

The plugin automatically sanitizes to: `My-New-Feature.md`

## 📂 Project Structure

```
cc-save-plan/
├── .claude-plugin/
│   └── plugin.json              # Plugin manifest and metadata
├── commands/
│   └── it.md                    # Slash command definition and logic
├── LICENSE                      # MIT License
└── README.md                    # This file
```

## 💡 Use Cases

- **Version Control**: Keep implementation plans with your code in git
- **Documentation**: Maintain planning documents alongside code
- **Team Collaboration**: Share architectural plans with team members
- **Project History**: Track how features were planned over time
- **Code Reviews**: Reference plans during PR reviews

## 🔍 Error Messages

| Message | Meaning | Solution |
|---------|---------|----------|
| `Usage: /stash:it <plan_name>` | No plan name provided | Provide a name: `/stash:it my-plan` |
| `No plan files found in ~/.claude/plans/` | No plans exist yet | Run `/plan` first to generate a plan |
| `Operation cancelled.` | User chose to cancel | Run the command again when ready |

## 🛠️ Requirements

- Claude Code CLI
- Bash shell
- Unix-like operating system (Linux, macOS)

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup

```bash
git clone https://github.com/hyeonsung/cc-save-plan.git
cd cc-save-plan
claude plugin link .
```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**hyeonsung**

- GitHub: [@hyeonsung](https://github.com/hyeonsung)

## 🔗 Links

- [GitHub Repository](https://github.com/hyeonsung/cc-save-plan)
- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Report Issues](https://github.com/hyeonsung/cc-save-plan/issues)
- [Request Features](https://github.com/hyeonsung/cc-save-plan/issues/new)

## 🙏 Acknowledgments

- Built for the Claude Code ecosystem
- Inspired by the need for better plan management in development workflows

---

<div align="center">

**If you find this plugin helpful, please consider giving it a ⭐️!**

Made with ❤️ by hyeonsung

</div>
