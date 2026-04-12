+++
title = "WorkWindow"
date = 2026-04-11T10:00:00-05:00
draft = false
description = "A planning workspace that combines a to-do list, Kanban flow, and calendar scheduling in one React and Vite interface, with dual launch options for local use or Supabase-backed sync."
summary = "A planning workspace that combines a to-do list, Kanban board, and calendar view, with dual launch options for local use or Supabase-backed sync."
image = "/images/projects/workwindow-board-overview.svg"
hideFeaturedImage = true
showInHome = true
toc = true
tags = ["React", "Vite", "Supabase", "Local-First", "Productivity", "Frontend"]
badges = ["React", "Vite", "Supabase", "dual launch", "Kanban", "Calendar"]
[[links]]
icon = "fab fa-github"
url = "https://github.com/acanave/WorkWindow"
+++

This showcase is based on the repository at [acanave/WorkWindow](https://github.com/acanave/WorkWindow). The project started from a real workflow gap: task lists, calendars, and Kanban boards each solve part of planning, but they often leave the actual delivery picture scattered across separate tools. WorkWindow brings those views together into one interface so planning, status, and execution can be understood in the same place.

## Why this project is worth showcasing

Many productivity apps can demo a board or a calendar in isolation. WorkWindow is more interesting as a portfolio project because it treats planning as a systems problem instead of a single-screen UI problem.

| Area | What WorkWindow does | Why it matters |
| --- | --- | --- |
| Planning model | Combines Kanban, calendar scheduling, and progress signals | Shows product thinking beyond CRUD task management |
| Runtime model | Works locally first with no backend dependency | Makes the app useful immediately and easier to evaluate |
| Upgrade path | Adds optional Supabase-backed auth and sync | Demonstrates architectural flexibility instead of hard backend coupling |
| Engineering depth | Uses normalized state, migration scaffolding, and tests | Turns a UI concept into a durable frontend system |

That mix makes the repo a strong showcase of both product judgment and frontend engineering discipline.

## Architecture

![WorkWindow board overview](/images/projects/workwindow-board-overview.svg)

WorkWindow is built as a **React + Vite** application with a local-first user experience. The default path is intentionally lightweight: the planner can run fully in the browser, persist state locally, and stay useful without external infrastructure.

The architecture also leaves room for a more production-oriented mode. When Supabase is configured, the same planning state can be hydrated into an authenticated user flow with cloud-backed persistence. That creates a clean progression from immediate local evaluation to multi-device access, without forcing the app to depend on backend services just to be usable.

The repo also shows careful deployment posture around that split:

- local mode works without secrets or service setup
- cloud mode uses publishable frontend configuration only
- hosted deployments can add auth and sync without changing the core planning model
- security headers and deploy-ready configuration are included for the hosted path

## Product highlights

WorkWindow is designed to give a clearer picture of delivery than a plain task list can provide.

- A Kanban board tracks work across Backlog, In Progress, Blocked, and Done.
- A month calendar shows planned work blocks so effort is visible over time, not just in a queue.
- Dependency warnings and chain visibility help surface sequencing risk before it turns into delay.
- Due-date signals and shortfall indicators make schedule pressure visible inside the product.
- JSON import and export keep the local-first workflow portable.
- Touch-friendly fallback actions support planning flows even where richer interactions are limited.

The result is a planner that feels focused on execution, not just item storage.

## Engineering highlights

WorkWindow is also a solid frontend engineering artifact because the implementation goes beyond a polished surface.

- Application state is normalized instead of being scattered across ad hoc component state.
- Schema migration scaffolding makes future evolution of stored data more manageable.
- A reusable reducer and store setup supports import replacement and state transitions cleanly.
- Optional cloud bootstrap logic hydrates local state from Supabase without changing the main product model.
- Test coverage focuses on state behavior, calendar interactions, dependency views, and planning fallbacks.

That structure makes the repo useful in a technical discussion because it shows how product behavior is supported by a maintainable internal model.

## Launch paths

![WorkWindow mode chooser](/images/projects/workwindow-mode-chooser.svg)

WorkWindow supports two clear evaluation paths.

### Local-first mode

This is the fastest way to understand the product. The app runs with browser storage only, which means the full planner can be reviewed without provisioning any services. That makes the project especially strong as a portfolio piece because the core experience is accessible immediately.

### Cloud-sync mode

The second path adds Supabase authentication and persistence for a hosted, multi-device workflow. That path demonstrates that the project is not just a local prototype: it has a practical route toward authenticated sync, user-scoped state, and a more production-oriented deployment shape.

## Repository

- GitHub: [WorkWindow](https://github.com/acanave/WorkWindow)
- README: [Project overview and setup notes](https://github.com/acanave/WorkWindow/blob/main/README.md)

## Key takeaway

The strongest part of WorkWindow is not just that it looks polished. It shows how a real product idea can be shaped into a local-first application with a credible cloud upgrade path, while still keeping the user experience fast, understandable, and easy to evaluate.
