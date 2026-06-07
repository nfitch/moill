# lists / moill: Project Overview

## Project Name

Current: **lists**
Future: **moill** (Map of Indexed Linked Lists)

## Problem Statement

Most list and note-taking tools require constant context-switching between keyboard and mouse, breaking the user's flow. When managing and reorganizing lists of things, that friction compounds quickly.

list-prime solves this by being entirely keyboard-driven, with shortcuts intuitive enough that the learning curve is shallow — the interface gets out of the way.

## Ultimate Vision

A real-time collaborative lists experience — multiple people editing lists in tandem, at the speed of talking and thought. The gold standard is Excalidraw: fluid, instantaneous, no friction, works with multiple people simultaneously.

This necessarily requires a distributed systems architecture. It will be a significant engineering undertaking.

## What We're Doing Now

1. **Consolidate** — gather all thinking from prior iterations (node-moill, node-list, list-claude prototype, index.html TODOs) into this repo as design documents. Keep what's still valid, rethink what prior knowledge changes, discard the rest.
2. **Roadmap** — create a project checklist that tracks the path from prototype to the full collaborative vision.
3. **Code quality** — this codebase will be maintained by humans, written by both nf and Claude. Code quality is a hard requirement. Technical controls (tests, linting, conventions) must ensure Claude's non-determinism doesn't accumulate into unmaintainable code.

## Code Quality Requirements

This is not a throwaway prototype. Both nf and Claude will write code here, and it must all be maintainable by a human.

- Every module must have tests
- Code must be readable and self-evident without Claude's context
- Consistent conventions enforced by tooling, not goodwill
- No clever shortcuts that trade readability for brevity
- Technical controls TBD during architecture phase

## Project Tracking

- `project/checklist.md` — master roadmap, phases and milestones
- `project/checklists/*.md` — individual phase checklists
- These are kept current at all times; Claude updates them as work progresses

## Design Philosophy

**"Add and move things within and between lists at the speed of thought."**

This is the singular design goal. Everything else is secondary to it. Concretely, this means:

- **Zero lag.** Any perceptible delay breaks the user's flow. The app must feel instantaneous.
- **No mouse required.** Every action must be reachable via keyboard. Moving hands to the mouse is a flow-breaker.
- **Intuitive key mappings.** The commands must be learnable quickly. Shallow learning curve is a hard requirement, not a nice-to-have.
- **Remappable shortcuts.** Users have different muscle memory. Every action shortcut must be remappable per user.

Reference: Excalidraw is the gold standard for this kind of "at the speed of thought" UX.

## Technical Constraints

- **Vanilla JS / HTML / CSS only.** No frameworks, no build system, no dependencies.
  - Rationale: frameworks add overhead (bundle size, runtime cost, abstraction layers). Zero-lag requires zero-overhead.
  - This constraint is non-negotiable.
- **Static site.** No server-side component. Runs entirely in the browser.
- **localStorage for persistence.** No network calls in the critical path.

## Prior Iterations

This project has been started several times:

1. **node-moill** (`../node-moill`) - Node.js server + REST API + mouse-driven UI. Abandoned. Had a fully implemented and tested `IndexedLinkedList` data structure.
2. **node-list** (`../node-list`) - Second server attempt (Fastify), barely started. Has a complete REST API design.
3. **list-claude** (this repo) - Pivot to vanilla JS static site + keyboard-driven UI. Working prototype.

### Key Asset: IndexedLinkedList (from node-moill)

Doubly linked list + hash map. All operations O(1): `insertBefore`, `insertAfter`, `moveBefore`, `moveAfter`, `remove`, `get`, `exists`. Has a full test suite. This is the intended backing data structure for lists and element ordering.

The current prototype uses the DOM as its implicit data structure — element order is stored in DOM node order. The eventual implementation replaces this with an explicit `IndexedLinkedList`.

### Key Concept: Views (from node-list API)

A **View** is an ordered collection of Lists. A List can appear in multiple Views. This separates:
- What lists/elements exist (the data)
- How they are arranged on screen (the view)

This is the intended model for the workspace: users work within a View, which references an ordered set of Lists.

### node-list REST API Summary

The node-list API (`../node-list/api/README.md`) is the most complete design artifact. Key resources:

| Resource | Operations |
|---|---|
| Users | CreateOrUpdate |
| Lists | CreateOrUpdate, Get, Delete, ListAll, Clone |
| Elements | Create, Get, Update, Move (before/after/index, cross-list), Delete |
| Views | CreateOrUpdate, Get, Delete, AddList, RemoveList, MoveList, Clone |

All element/list positions specified as: end (default), by index, after id, or before id.

## Current State (Prototype)

The existing code is a working prototype that proves out the core concept. It is day-to-day usable (as of ~2023). Key features implemented:

- Multi-list layout (horizontal, flex-based)
- Keyboard navigation: arrow keys to select up/down/left/right
- Keyboard movement: Ctrl+Shift+arrows (or Meta+Shift+arrows) to move elements/lists
- Type Mode: printable characters typed directly into selected element
- Cut / Copy / Paste (internal to app, not system clipboard)
- Save/Load/Merge via JSON file
- Auto-save to localStorage every 3 seconds
- Remappable key bindings (architecture in place, not yet surfaced to user)
- Help panel with action/key reference

## Source Layout

```
index.html                  Entry point, toolbar, init wiring
list/
  lists.js                  Core: selection, DOM manipulation, cut/copy/paste, storage
  list-parser.js            JSON serialization (v0, v1 formats)
  key-handler.js            Key binding system, help panel generation
  list-styling.css          All styling
  sample-data/              Test JSON files (various format versions)
design/                     Architecture and design documentation
```

## Data Format (v1 JSON)

```json
{
  "version": 1,
  "lists": [
    {
      "elements": [
        { "data": "element text" }
      ]
    }
  ]
}
```

Older formats (unversioned, v0) are parsed and upgraded on load.
