# Contributing to Save Plan Plugin

Thank you for your interest in contributing! This document provides guidelines for contributing to the Save Plan Plugin for Claude Code.

## 🤝 How to Contribute

### Reporting Bugs

If you find a bug, please create an issue using the bug report template. Include:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Your environment (OS, Claude Code version, shell)

### Suggesting Features

Feature requests are welcome! Please:
- Check existing issues first to avoid duplicates
- Use the feature request template
- Explain the use case and benefits
- Be open to discussion and feedback

### Submitting Pull Requests

1. **Fork the repository**
   ```bash
   # Click "Fork" on GitHub, then clone your fork
   git clone https://github.com/YOUR_USERNAME/cc-save-plan.git
   cd cc-save-plan
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

3. **Make your changes**
   - Follow the existing code style
   - Test your changes thoroughly
   - Keep commits focused and atomic

4. **Test locally**
   ```bash
   # Link the plugin for testing
   claude plugin link .

   # Test the command
   /stash:it test-plan
   ```

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add new feature description"
   # or
   git commit -m "fix: fix bug description"
   ```

6. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Open a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Fill out the PR template completely
   - Link any related issues

## 📝 Commit Message Guidelines

We follow conventional commits:

- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting, no logic change)
- `refactor:` - Code refactoring
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks

**Examples:**
```
feat: add option to specify custom output directory
fix: handle spaces in plan filenames correctly
docs: update installation instructions
```

## 🔍 Code Review Process

1. All PRs require review from the maintainer
2. Address review feedback promptly
3. Keep discussions professional and constructive
4. Once approved, the maintainer will merge your PR

## 📋 PR Checklist

Before submitting, ensure:
- [ ] Code follows existing style and conventions
- [ ] Tested manually with various scenarios
- [ ] Documentation updated (README, comments)
- [ ] Commit messages follow guidelines
- [ ] PR description is clear and complete

## 🐛 Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/cc-save-plan.git
cd cc-save-plan

# Link for local testing
claude plugin link .

# Make changes and test
/stash:it test

# Unlink when done
claude plugin unlink stash
```

## 📚 Project Structure

```
cc-save-plan/
├── .claude-plugin/
│   ├── plugin.json          # Plugin metadata
│   └── marketplace.json     # Marketplace listing info
├── commands/
│   └── it.md                # Main command logic (bash)
├── plugins/stash/           # Nested plugin structure
│   ├── .claude-plugin/
│   ├── commands/
│   └── README.md
├── CONTRIBUTING.md          # This file
├── CODE_OF_CONDUCT.md       # Community guidelines
└── README.md                # Main documentation
```

## 🎯 What We're Looking For

Great contributions include:
- Bug fixes with clear reproduction steps
- Performance improvements
- Better error handling
- Improved user experience
- Documentation improvements
- Cross-platform compatibility fixes

## ❌ What to Avoid

Please don't:
- Submit PRs without testing
- Make large, unfocused changes
- Ignore maintainer feedback
- Break existing functionality
- Add unnecessary dependencies

## 💬 Questions?

- Open a discussion in Issues
- Tag your issue with `question`
- Be patient and respectful

## 🙏 Thank You!

Your contributions make this project better for everyone. We appreciate your time and effort!

---

**Note:** The maintainer reserves the right to reject PRs that don't align with the project's goals or quality standards. This is not personal - we want to keep the codebase maintainable and focused.
