# The 80 Engine — deploy bundle

Two files. They are the same document; the difference is what a reader can find in the page source.

| File | Who it's for | Contains |
|---|---|---|
| `index.html` | Donors, partners, anyone outside the core team | The ten-tab brief. No presenter notes anywhere — not hidden, **not in the source at all**. |
| `presenter.html` | The team, internal only | Everything above, plus the talk track, objection handling, donor archetypes, and the "don't get caught out" list. Presenter mode toggles with the button or Shift+P. |

## Why two files

In the single-file version, the talk track was hidden by CSS but still sat in the HTML. Anyone who opened View Source — including a donor you sent the link to — could read the objection handling and the coaching notes. That's now fixed by separation rather than concealment: `index.html` genuinely does not contain them.

**Never publish `presenter.html` to the same place as `index.html`.** Keep it in the repo, on a share drive, or on a separate protected path.

## Deploying behind the password gate

Put `index.html` where the existing gate already runs (the80investments.com), not on GitHub Pages.

GitHub Pages serves static files only and has no server-side authentication. A JavaScript password prompt on a Pages site is obfuscation, not protection — the password and the whole document are in the source, readable by anyone with the URL. Given this file contains named salary bands, that is not good enough.

The existing gate issues a key (`/gate?k=…`) before serving content, which means real server-side access control. Ask KB which platform it runs on and deploy there. If a new path is needed, `index.html` is self-contained — no build step, no assets, no dependencies. Drop it in and point the gate at it.

## If it does go on GitHub

Use a **private** repo for both files. Private repos need GitHub Pro, Team or Enterprise to serve Pages; on a free account, enabling Pages makes the repo public.

```
git init
git add index.html README.md
git commit -m "The 80 Engine — donor brief"
git branch -M main
git remote add origin git@github.com:<account>/<repo>.git
git push -u origin main
```

Then Settings → Pages → Source: `main` / root.

## What's in the document

Budget figures are **people only** — salaries and benefits from the 2027 staff plan. Software, NYC travel and equipment are excluded, which is what makes a state land at $1.25M rather than $1.26M. National is $3.165M; six states plus national is $10.65M, reconciling to the staff plan.

Not yet resolved, and flagged inside the document:

- Performance targets / KPIs are marked "in development"
- The80 Live is marked "proposed" and is not costed
- No state list is committed — the slider shows scale, not named states
- Next Steps is marked draft pending governance confirmation
- Research from the C3/C4 document has not been merged in
