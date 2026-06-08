# lists / moill — Project Checklist

Master roadmap. Kept current as work progresses.

---

## Phase 1: Repo Consolidation
> Gather all thinking from prior iterations into this repo.

- [ ] See `project/checklists/phase-1-repo-consolidation.md`
- Note: prior repo inventory (what to bring over vs discard) is tracked in the phase-1 checklist and evaluated in Phase 4

## Phase 2: Extract TODOs / Build Finer-Grained Checklist
> Pull TODOs from index.html and prior repos. Build a detailed checklist for Phase 3.

- [ ] See `project/checklists/phase-2-extract-todos.md`

## Phase 3: Teach Claude the Codebase
> Work through the prototype TODO list. Get Claude productive in the existing code.
> This includes tests, conventions, and enough context that Claude can write maintainable code here.

- [ ] See `project/checklists/phase-3-teach-claude.md`

## Phase 4: Server Prototype — Single User
> Add a backend. Single-user experience backed by a server rather than localStorage.

- [ ] See `project/checklists/phase-4-server-single-user.md`
- [ ] Evaluate prior repo artifacts for reuse — see inventory in `project/checklists/phase-1-repo-consolidation.md`

## Phase 5: Server Prototype — Multi User
> Extend server to support multiple users. Basic real-time collaboration.

- [ ] See `project/checklists/phase-5-server-multi-user.md`

## Phase 6: UI Polish
> Clean up the UI for the prototype. Good enough to use and share.

- [ ] See `project/checklists/phase-6-ui-polish.md`

---

## >> PROTOTYPE COMPLETE GATE <<

Everything above this line is prototype work. Below is the real thing.

---

## Phase 7: Redesign the User Experience
> Rethink UX from scratch with full collaborative vision in mind.

- [ ] See `project/checklists/phase-7-ux-redesign.md`

## Phase 8: Redesign the APIs
> Rethink APIs with production requirements: concurrency, multi-user, performance.

- [ ] See `project/checklists/phase-8-api-redesign.md`

## Phase 9: Architecture
> Full distributed systems architecture for real-time multi-user collaboration at scale.

- [ ] See `project/checklists/phase-9-architecture.md`

## Phase 10: Rework Project Checklist — Build the Real Thing
> After Phases 7-9, rebuild this checklist with what we actually know.

- [ ] Revisit and rewrite this checklist based on design output from Phases 7-9
