# claude-tools

A collection of command-line tools for working with [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Tools

### claude-browse

Interactive TUI for browsing, searching, resuming, and forking Claude Code sessions.

Reads your local `~/.claude/projects` directory and presents all sessions across projects in a navigable interface with full-text search, conversation history viewing, and one-key resume or fork (resume into a new session ID, leaving the original untouched).

**Install:**

```sh
# Copy or symlink to somewhere on your PATH
cp claude-browse /usr/local/bin/
# or
ln -s "$(pwd)/claude-browse" /usr/local/bin/claude-browse
```

**Requirements:** Python 3.7+, Claude Code CLI

**Quick start:**

```sh
claude-browse                          # interactive session browser
claude-browse -s "search term"         # open with search results
claude-browse -n 20                    # show 20 most recent sessions
claude-browse --session ID --history   # print a session's conversation to stdout
claude-browse --session ID --fork      # fork a session into a new session ID
claude-browse --json                   # dump session list as JSON
```

History output renders markdown tables as box-drawn tables sized to your terminal (with bold/italic/code spans as ANSI styling), matching how Claude Code displays them in a live conversation. Pass `--no-tables` to leave the raw markdown alone.

**Environment variables:**

- `CLAUDE_BROWSE_CMD` — command used to resume sessions (default: `claude`). Set this if your binary has a different name or to pass default CLI flags, e.g. `CLAUDE_BROWSE_CMD="claude --dangerously-skip-permissions"`.

See the top of the `claude-browse` script for full flag and keybinding reference.
