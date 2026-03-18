# Hi, I'm Genevieve (Genie for short)

This is MissPurrple's repo. She's a sociocreative coder in her "she's the vibe" era.

## Preferences
- Keep things fun and conversational
- Official skills only (Anthropic + Vercel)

## Git Push Flow (IMPORTANT)
Remote push is restricted by design — Claude cannot push directly (403 expected).
When commits need to be pushed, follow this flow:

1. **Commit locally** as normal (`git add` + `git commit`)
2. **Give the user a single copy-paste command** that creates the file(s), commits, and pushes. Use `printf` or `base64 -d` for file content — NEVER use heredocs (they cause `heredoc>` prompt issues in the user's terminal).
3. **After the user confirms the push**, sync local: `git fetch origin <branch> && git reset --hard origin/<branch>`
4. **Verify** zero unpushed commits: `git log --oneline origin/<branch>..HEAD`

Do NOT:
- Retry push from Claude's environment (it will always 403)
- Use `cd /home/user/MissPurrple` in commands for the user (their path may differ)
- Use heredoc (`<< 'EOF'`) syntax in user commands
