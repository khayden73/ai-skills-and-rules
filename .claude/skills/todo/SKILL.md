---
name: todo
argument-hint: [action] [text]
description: manage a project TODO list — add, list, complete, or remove items in TODO.md
user-invocable: true
---

**action** is one of: `add`, `list`, `done`, `remove` (case-insensitive)  
**text** is the TODO description (for `add`), or an item number or partial match (for `done`/`remove`)

**TODO.md** lives at the project root and should be created if it does not exist.

## File Format

Items use GitHub-flavored markdown checkboxes with inline metadata:

```
- [ ] Description `priority` `category` _YYYY-MM-DD_
- [x] Description `priority` `category` _YYYY-MM-DD_ → _YYYY-MM-DD_
```

- Unchecked `[ ]` = open; checked `[x]` = resolved
- Priority values: `high`, `medium`, `low`
- Category is a free-form tag (e.g. `bug`, `feature`, `refactor`, `chore`)
- First date is **date added**; second date (after `→`) is **date resolved** — only present on completed items
- Items are referenced by their 1-based position in the file for `done` and `remove`

## Actions

### add
Append a new TODO item at the bottom of the open items. If priority or category are not supplied as arguments, ask for them before writing.

### list
Display all items in TODO.md grouped by status (open first, then resolved). If the file does not exist, say so. Accept optional filter arguments: `open`, `done`, a priority level (`high`/`medium`/`low`), or a category tag.

### done
Mark an item complete. Match by 1-based item number or partial description. Set `[x]` and append `→ YYYY-MM-DD` with today's date. If multiple items match a partial description, list them and ask which one.

### remove
Delete an item entirely without marking it done. Match by item number or partial description. Confirm with the user before deleting. If multiple items match, list them and ask which one.

## Warnings
- If `done` or `remove` is run and the file has no items, alert the user
- If no match is found for `done` or `remove`, alert the user

## Committing
Do **not** auto-commit. Leave TODO.md unstaged for the user to commit manually.
