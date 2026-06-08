# Phase 1: Repo Consolidation

Gather all thinking from prior iterations into this repo as design documents.

---

## Tasks

- [x] Create `design/01-project-overview.md` with project context, vision, prior iterations
- [x] Create `project/checklist.md` master roadmap
- [x] Bring in node-list API design as `design/02-api-design.md`
- [x] Extract TODOs from `index.html` — Phase 2
- [x] Extract TODOs from `node-moill/TODO` — Phase 2

---

## Prior Repo Inventory

Track what has and hasn't been brought over from prior iterations.
To be evaluated in Phase 4 (Server Prototype — Single User).

### node-moill (`../node-moill`)

| Artifact | Status | Notes |
|---|---|---|
| `lib/indexed-linked-list.js` | Deferred to Phase 4 | Core ILL data structure, fully implemented |
| `test/test-indexed-linked-list.js` | Deferred to Phase 4 | Full test suite for ILL |
| `lib/moill-actions.js` | Discard | Server approach abandoned |
| `lib/moill-server.js` | Discard | Server approach abandoned |
| `lib/moill-config.js` | Discard | Server approach abandoned |
| `lib/moill.js` | Discard | Server approach abandoned |
| `TODO` | Done | Folded into phase-2 checklist |

### node-list (`../node-list`)

| Artifact | Status | Notes |
|---|---|---|
| `api/README.md` | Done | Captured in `design/02-api-design.md` |
| `lib/indexed-linked-list.js` | Deferred to Phase 4 | Newer version of ILL — compare with node-moill version |
| `test/indexed-linked-list.test.js` | Deferred to Phase 4 | Test suite — compare with node-moill version |
| `lib/list-server.js` | Discard | Fastify stub, nothing there |
| `static/` | Discard | Styling experiments, superseded by list-claude |
