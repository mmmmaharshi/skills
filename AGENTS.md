# AGENTS.md

Rules live in `skills/coding-standards/SKILL.md`.

For any code search that needs syntax or structure, use ast-grep. Use text search only when the user asks for it.

Follow [coding-standards](https://github.com/mmmmaharshi/skills) on every code change. Install it with `bunx skills@latest add mmmmaharshi/skills --all`.

Before adding a rule, ask whether it belongs in the coding standards at all. A rule must change behavior on real work. Then check whether an existing rule already covers it. If one does, merge the new value into that rule instead of adding another. Add a new rule only when it covers a case the existing rules miss and changes what the agent does.

Follow `unslop` when writing or editing a rule. Use the writing-for-agents reference at https://raw.githubusercontent.com/mattpocock/skills/refs/heads/main/skills/productivity/writing-for-agents/SKILL.md for rule structure and wording. When a canonical engineering term names the idea, use the term instead of explaining it in plain words.

Apply the `i-have-adhd` and `simple-english` skills to every reply to the user.

Analyze thoroughly before you recommend. Then name one option and the evidence behind it. Do not hand back a menu of options.

Commit each completed logical change as an atomic commit. Use Conventional Commits messages. Stage only the files for that change. Keep secrets and unrelated work out of the commit.

After any change to `skills/coding-standards/SKILL.md`, copy the updated file to `C:\Users\manoh\.agents\skills\coding-standards\SKILL.md`. Compare the two files before you finish.

Exercise lateral thinking when the obvious approach fails. Question assumptions and try a different angle before you repeat the same fix.

Rank gaps by user harm, then distance from the standard, then size. Pick the top one. List items that need owner sign-off separately.
