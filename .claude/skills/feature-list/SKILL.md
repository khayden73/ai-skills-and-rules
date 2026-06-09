# feature-list

Capture and track feature ideas as they come up during development or testing.

**FEATURES.md** lives at the project root and should be created if it does not exist.

## File Format

```
- [ ] Description `priority` `tag` _YYYY-MM-DD_
- [~] Description `priority` `tag` _YYYY-MM-DD_
- [x] Description `priority` `tag` _YYYY-MM-DD_ → shipped _YYYY-MM-DD_
- [-] Description `priority` `tag` _YYYY-MM-DD_ → dropped _YYYY-MM-DD_
```

### Status symbols

| Symbol | Meaning |
|--------|---------|
| `[ ]` | idea |
| `[~]` | planned |
| `[x]` | shipped |
| `[-]` | dropped |

### Priority values
`required` `nice-to-have`

### Tag values
`ux` `ui` `data` `integration` `automation` `analytics` `nav`

- Items are referenced by their 1-based position in the file for `plan`, `shipped`, `drop`, and `remove`
- First date is **date added**; resolved items append `→ shipped` or `→ dropped` with the resolution date

## Actions

### add
Append a new feature idea at the bottom of the open items. If priority or tag are not supplied as arguments, ask for them before writing.

### list
Display all features in FEATURES.md grouped by status in this order: idea, planned, shipped, dropped. If the file does not exist, say so.

Accept optional filter arguments:
- Status: `idea`, `planned`, `shipped`, `dropped`
- Priority: `required`, `nice-to-have`
- Tag: `ux`, `ui`, `data`, `integration`, `automation`, `analytics`, `nav`

### plan
Mark a feature idea as planned. Change `[ ]` to `[~]`. Match by 1-based item number or partial description. If multiple items match a partial description, list them and ask which one.

### shipped
Mark a feature as shipped/done. Change the status symbol to `[x]` and append `→ shipped _YYYY-MM-DD_` with today's date. Match by 1-based item number or partial description. If multiple items match, list them and ask which one.

### drop
Mark a feature as dropped/won't do. Change the status symbol to `[-]` and append `→ dropped _YYYY-MM-DD_` with today's date. Match by 1-based item number or partial description. If multiple items match, list them and ask which one.

### remove
Delete a feature entirely without changing its status. Match by item number or partial description. Confirm with the user before deleting. If multiple items match, list them and ask which one.

## Warnings
- If `plan`, `shipped`, `drop`, or `remove` is run and the file has no items, alert the user
- If no match is found, alert the user
- If `shipped` or `drop` is run on an already-closed item, confirm before overwriting

## Committing
Do **not** auto-commit. Leave FEATURES.md unstaged for the user to commit manually.
