# issue-tracker

Track issues found during product testing — UX problems, UI defects, bugs, and other observations.

**ISSUES.md** lives at the project root and should be created if it does not exist.

## File Format

ISSUES.md uses markdown tables grouped by priority section, most severe first. Each section only appears if it has at least one item.

```markdown
# Issues

## Critical

| Date | Issue | Tag | Status |
|------|-------|-----|--------|
| YYYY-MM-DD | Description | `tag` | open |

## High

| Date | Issue | Tag | Status |
|------|-------|-----|--------|
| YYYY-MM-DD | Description | `tag` | open |

## Medium

| Date | Issue | Tag | Status |
|------|-------|-----|--------|
| YYYY-MM-DD | Description | `tag` | open |

## Low

| Date | Issue | Tag | Status |
|------|-------|-----|--------|
| YYYY-MM-DD | Description | `tag` | open |
```

### Status values (in the Status column)

| Value | Meaning |
|-------|---------|
| `open` | Open |
| `in progress` | In progress |
| `fixed → YYYY-MM-DD` | Closed — fixed (append resolution date) |
| `wontfix → YYYY-MM-DD` | Closed — won't fix (append resolution date) |

### Priority values (section headers)
`Critical` `High` `Medium` `Low`

### Tag values
Common tags: `ux` `ui` `bug` `copy` `a11y` `perf` `nav`. These are suggestions, not a restriction — other descriptive tags (e.g. `deployment`, `security`) are allowed when they fit better.

- Items are referenced by their 1-based position counted across all table rows in the file (ignoring section headers and table separator rows)
- The Date column holds the date the issue was added

## Default behavior

If invoked with no arguments, display the list of available commands (same output as `help`):

```
/issue-tracker add <description> [-p priority] [-t tag]   Add a new issue (prompts for missing priority/tag)
/issue-tracker list [status] [priority] [tag]       List issues, optionally filtered
/issue-tracker start <number|partial>               Mark an issue in progress
/issue-tracker fixed <number|partial>               Mark an issue closed — fixed
/issue-tracker wontfix <number|partial>             Mark an issue closed — won't fix
/issue-tracker remove <number|partial>              Delete an issue entirely (confirms first)
```

Also display this help output when the argument is literally `help`.

## Actions

### add
Insert a new row into the correct priority section. If priority or tag are not supplied, ask for them interactively before writing. If the section for that priority does not exist yet, create it in the correct order (Critical → High → Medium → Low).

Priority and tag may be supplied inline using flags anywhere after the description:

```
/issue-tracker add Description here --priority high --tag ux
/issue-tracker add Description here -p high -t ux
```

Flags:
- `--priority` / `-p` — one of: `critical`, `high`, `medium`, `low`
- `--tag` / `-t` — any short descriptive tag, e.g. `ux`, `ui`, `bug`, `copy`, `a11y`, `perf`, `nav`, `deployment`, `security`

If `--priority` is not one of the four allowed values, do not guess or proceed — prompt the user to pick a valid value before writing. Tags are not restricted to a fixed list.

### list
Display all issues grouped by priority (Critical → High → Medium → Low), using the table format above. If the file does not exist, say so.

Accept optional filter arguments:
- Status: `open`, `in-progress`, `closed`
- Priority: `critical`, `high`, `medium`, `low`
- Tag: any tag value present in the file

### start
Mark an open issue as `in progress`. Update the Status cell from `open` to `in progress`. Match by 1-based item number or partial description. If multiple items match a partial description, list them and ask which one.

### fixed
Mark an issue as `fixed → YYYY-MM-DD`. Update the Status cell with today's date. Match by 1-based item number or partial description. If multiple items match, list them and ask which one.

### wontfix
Mark an issue as `wontfix → YYYY-MM-DD`. Update the Status cell with today's date. Match by 1-based item number or partial description. If multiple items match, list them and ask which one.

### remove
Delete a row entirely without changing its status. Match by item number or partial description. Confirm with the user before deleting. If multiple items match, list them and ask which one. Remove the section header too if it becomes empty.

## Warnings
- If `start`, `fixed`, `wontfix`, or `remove` is run and the file has no items, alert the user
- If no match is found, alert the user
- If `fixed` or `wontfix` is run on an already-closed issue, confirm before overwriting

## Committing
Do **not** auto-commit. Leave ISSUES.md unstaged for the user to commit manually.
