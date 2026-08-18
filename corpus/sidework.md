# Sidework — the collection beside the main projects

*One structured folder on this machine collecting, in one place, the parts that matter from every side repo — research results, notes, references — plus quick jottings. It lives here and only here: a plain local folder, nothing scheduled, nothing running in the background.*

## Layout

```
~/sidework/
  <repo-name>/…        # one section per side repo, holding copies of its declared parts
  people/              # jottings: people met, contact notes
  ideas/               # jottings: ideas worth keeping
  notes/               # jottings: everything else notable
  grab.manifest        # what gets collected (see below)
  grab                 # the collection script
```

- **Sections hold real copies, not links** — the folder is self-contained; everything in it is directly there.
- **Jot sections are ordinary files:** the agent or the owner appends people met, ideas, and notables as they come up, at whatever grain is convenient. Full sentences preferred over fragments.

## The grab

`./grab` (run it on the owner's ask — "refresh sidework" — or at the end of a working session; never on a schedule):

1. For each entry in `grab.manifest` (one line: `<repo path> → <subpath, …> → <section>`), copy every file that is **new or changed since the last grab** into the section — `rsync -a --update` per declared subpath, **never `--delete`**: the collection only grows; nothing is ever removed by the grab.
2. Print a short report of what arrived (new and updated files per section) — the report doubles as the owner's what's-new view over his side work.
3. Where the owner wants an aggregate page (e.g. all experiment results across repos on one page), the agent renders it into the relevant section on ask.

## Scope

- Sources are **side repos only** — the repos of the owner's own projects present on this machine — and only their manifest-declared parts ("part of some repos" is the point: declare `results/` and `notes/`, not the whole tree).
- Employer project content stays in employer systems and never enters sidework (the standing IP rule); sidework is precisely the shelf for everything that is *not* the main job.

## Setup (first use)

The agent creates the folder, `grab.manifest`, and the `grab` script (a small wrapper implementing the two steps above) when the owner first asks for sidework; the manifest starts from whichever side repos are present and the owner's word on which parts matter.
