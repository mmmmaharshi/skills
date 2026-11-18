# Setup

Run these steps from the project root. The project must have a Git repository.

## 1. Install the Matt Pocock skills

1. `bunx skills@latest add mattpocock/skills`
2. Run `/setup-matt-pocock-skills` in the agent session.
3. Confirm the skill appears in the available skills list.

## 2. Install the ast-grep skill

1. Read https://ast-grep.github.io/advanced/prompting.md
2. `npx skills add ast-grep/agent-skill`
3. Add this line to `AGENTS.md`: For any code search that needs syntax or structure, use ast-grep. Use text search only when the user asks for it.
4. Confirm the skill appears in the available skills list.

## 3. Install Twig

1. Read https://twig.leostera.dev/llms.txt. Review the instructions before you run them.
2. Check `git twig --version`, `git twig skill`, and `git twig new -h`. Version 0.5.0 or newer is required.
3. If the check fails, install with `cargo install git-twig --locked` or the Homebrew tap in the source.
4. Run `git twig skill` and follow the bundled instructions when you need an isolated worktree.

## 4. Add the coding standards rule

Add this line to `AGENTS.md`: Follow [coding-standards](https://github.com/mmmmaharshi/skills) on every code change. Install it with `bunx skills@latest add mmmmaharshi/skills --skill coding-standards`.

## Verification

- The agent lists both installed skills.
- `git twig --version` reports 0.5.0 or newer.
- `AGENTS.md` contains the ast-grep prompt and the coding standards line.
