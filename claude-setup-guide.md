# Making Claude Remember Your Projects Automatically

## The CLAUDE.md File

Claude automatically reads any file named `CLAUDE.md` in your project directory when you start a conversation. This is perfect for maintaining project context across sessions.

## Best Practices for CLAUDE.md Files

### 1. Keep It Concise
- Quick overview (2-3 sentences)
- Current status and recent work
- Key files and their purposes
- Any critical context or decisions

### 2. Update Regularly
Include a section like:
```markdown
## Recent Sessions
- 2025-01-06: Added animal game, fixed voice settings
- 2025-01-05: Initial speech recognition tests
```

### 3. Include Key Information
```markdown
## Quick Start
- Main file: `index.html`
- Run: `npm start` or open in browser
- Deploy: `git push origin main` (auto-deploys)

## Project Structure
- `/src` - Source code
- `/docs` - Documentation
- `/tests` - Test files

## Important Context
- Using React 18.2
- No TypeScript by design
- Mobile-first approach
```

## Setting Up Automatic Documentation

### Option 1: Git Hooks (Automatic)
Create `.git/hooks/pre-commit`:
```bash
#!/bin/bash
# Auto-update CLAUDE.md with recent changes

echo "## Last Updated: $(date)" >> CLAUDE.md
echo "## Recent Changes:" >> CLAUDE.md
git log --oneline -5 >> CLAUDE.md
```

### Option 2: VS Code Extension
Install "Claude Assistant" or similar extensions that maintain project context.

### Option 3: Project Template
Create a template with CLAUDE.md:
```bash
# Create a template directory
mkdir ~/project-templates/claude-ready

# Add template files
cd ~/project-templates/claude-ready
touch CLAUDE.md README.md .gitignore

# Use for new projects
cp -r ~/project-templates/claude-ready/* /new-project/
```

## What to Include in Every CLAUDE.md

```markdown
# Project Name - Claude Context

## Overview
[1-2 sentences about what this project does]

## Current Task/Status
- [ ] Current focus
- [x] Completed items

## Key Commands
- Run: `command here`
- Test: `test command`
- Deploy: `deploy command`

## Architecture Decisions
- Why we chose X over Y
- Important constraints

## Common Issues & Solutions
- Issue: [description]
  Solution: [how to fix]

## External Resources
- API Docs: [link]
- Design: [link]

## Session History
- Date: What was done
```

## Global Setup for All Projects

### 1. Create a Global Template
```bash
# Create global Claude template
mkdir ~/.claude-templates
cat > ~/.claude-templates/CLAUDE.md << 'EOF'
# Project Context for Claude

## Overview
[Project description]

## Status
- Current version: 
- Last updated: 
- Next steps: 

## Quick Start
```
[Commands to run project]
```

## Key Files
- `file1` - Description
- `file2` - Description

## Notes for Claude
- 
EOF
```

### 2. Add Alias to Quickly Create CLAUDE.md
Add to `~/.bashrc` or `~/.zshrc`:
```bash
alias claude-init='cp ~/.claude-templates/CLAUDE.md ./CLAUDE.md && echo "CLAUDE.md created. Please edit with project details."'
```

### 3. Create a Git Alias
```bash
git config --global alias.claude '!echo "Creating CLAUDE.md..." && cp ~/.claude-templates/CLAUDE.md ./CLAUDE.md && git add CLAUDE.md && git commit -m "Add CLAUDE.md for context persistence"'
```

Now you can run `git claude` in any project!

## For This Project

I've created both:
1. `PROJECT_SUMMARY.md` - Comprehensive documentation
2. `CLAUDE.md` - Quick context for future Claude sessions

The CLAUDE.md file will be automatically read whenever you return to this project, ensuring I remember everything we've done!

## Tips for Effective Context Files

1. **Update After Major Changes**: Add a line about what was accomplished
2. **Include Gotchas**: Any tricky parts or non-obvious decisions
3. **Link to Resources**: Important URLs, documentation
4. **Keep It Current**: Old information can be misleading
5. **Be Specific**: "Uses AWS S3" is better than "cloud hosting"

Would you like me to create a script that automatically updates CLAUDE.md after each session?