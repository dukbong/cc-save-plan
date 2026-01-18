---
description: Save auto-generated plan files to your project
argument-hint: <plan_name>
allowed-tools: ["Bash", "AskUserQuestion"]
---

# Save Plan Command

Copy the latest auto-generated plan file from `~/.claude/plans/` to your project's `.claude/plan/` directory.

## Instructions

1. **Validate Arguments**
   - Check if a plan name was provided via `$ARGUMENTS`
   - If empty, respond with: "Usage: /stash:it <plan_name>"
   - Extract the plan name from `$ARGUMENTS`

2. **Sanitize Filename**
   - Remove special characters except alphanumeric, hyphens, and underscores
   - Ensure the filename ends with `.md` extension
   - Example: "My Plan!" becomes "My-Plan.md"

3. **Find Latest Plan File**
   - Search for the most recent `.md` file in `~/.claude/plans/`
   - Use: `ls -t ~/.claude/plans/*.md 2>/dev/null | head -1`
   - If no files found, respond with: "No plan files found in ~/.claude/plans/. Run /plan first."

4. **Create Target Directory**
   - Create `.claude/plan/` in the current working directory if it doesn't exist
   - Use: `mkdir -p "$(pwd)/.claude/plan"`

5. **Check for Duplicate Files**
   - Check if a file with the same name already exists in `.claude/plan/`
   - If it exists, use AskUserQuestion to ask the user:
     - Question: "A plan file named '[filename]' already exists. What would you like to do?"
     - Options:
       - "Overwrite the existing file"
       - "Save with a new version number (e.g., plan-name-v2.md)"
       - "Cancel the operation"

6. **Copy the File**
   - Based on user choice:
     - **Overwrite**: Copy directly to `.claude/plan/[name].md`
     - **Version**: Find the next available version number and save as `[name]-v[N].md`
     - **Cancel**: Exit with message "Operation cancelled."
   - Use: `cp "[source]" "$(pwd)/.claude/plan/[target].md"`

7. **Confirm Success**
   - Respond with: "Plan saved successfully to .claude/plan/[filename].md"
   - Include the full path for clarity

## Example

```
User: /stash:it feature-implementation

Output:
Plan saved successfully to .claude/plan/feature-implementation.md
Full path: /home/user/project/.claude/plan/feature-implementation.md
```

## Error Handling

- Invalid filename characters: Sanitize automatically
- No source files: Clear error message
- Directory creation fails: Report the error
- Copy operation fails: Report the error with details
