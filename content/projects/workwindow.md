+++
title = "WorkWindow"
date = 2026-04-11T10:00:00-05:00
draft = false
description = "A local-first planning workspace that unifies calendar scheduling, Kanban execution, and workload visibility, with an optional Supabase sync path."
summary = "A local-first planning workspace that unifies calendar scheduling, Kanban execution, and workload visibility, with an optional Supabase sync path."
image = "/images/projects/workwindow-board-overview.png"
hideFeaturedImage = true
showInHome = true
toc = true
tags = ["React", "Vite", "Local-First", "Kanban", "Calendar", "Supabase", "Testing", "Security"]
badges = ["React", "Vite", "Local-First", "Kanban", "Calendar", "Supabase"]
[[links]]
icon = "fab fa-github"
url = "https://github.com/acanave/WorkWindow"
+++

WorkWindow is a local-first planning workspace for people who want scheduling, execution, and workload visibility in one place. It keeps commitments, progress, and risk signals connected so planning feels clearer and more usable day to day.

The screenshots in this page are generated from a seeded demo workflow so the UI state stays consistent when reviewing the project.

## Why this matters

![WorkWindow calendar overview](/images/projects/workwindow-calendar-overview.png)
![WorkWindow board overview](/images/projects/workwindow-board-overview.png)

WorkWindow is useful because it treats planning as a connected workflow, not just a UI surface. The calendar, board, and workload view all support the same execution model, which makes the app easier to reason about and more useful in day-to-day use.

## Core capabilities

- Kanban board with Backlog, In Progress, Blocked, and Done lanes.
- Month calendar with due-date anchors and supporting work windows.
- Dependency warnings, chain visibility, and cycle badges.
- Due-date shortfall and overdue risk indicators.
- Performance panel with burnup, plan coverage, and weekly velocity.
- JSON import/export and local/cloud mode support.
- Touch-friendly fallback actions for planning and status changes.

## Technical snapshot

- React + Vite frontend with local-first state persistence.
- Optional Supabase Auth + Postgres sync path.
- Normalized reducer-driven state with migration scaffolding.
- Tests across store logic, calendar interactions, and Kanban flows.
- CI-gated quality checks with automated secret scanning.

## Optional cloud sync

When no cloud env vars are present, WorkWindow opens in local-first mode. If Supabase is configured, the same planner can sync authenticated state across devices without changing the core product model.

![WorkWindow mode chooser](/images/projects/workwindow-mode-chooser.png)

For setup details, see the README and cloud guide:

- [README](https://github.com/acanave/WorkWindow/blob/main/README.md)
- [Cloud sync setup](https://github.com/acanave/WorkWindow/blob/main/docs/cloud-setup.md)

## Implementation boundaries

WorkWindow is maintained as a public product repo, so the boundary is simple: keep the repo focused on product code and public-safe defaults.

- Include: UI, app logic, tests, docs, schema, migration scripts, and sample data.
- Exclude: personal secrets, bot tokens, private deployment credentials, personal automation scripts, and exported personal task data.
- Keep live app data in runtime storage, not in git.
- Keep `.env.example` as placeholders only, and leave `.env.local` untracked.
- Never expose service-only keys in Vite environment variables.

Links:

- [GitHub repository](https://github.com/acanave/WorkWindow)
- [README](https://github.com/acanave/WorkWindow/blob/main/README.md)

## Trust and Policies

- Security policy: [SECURITY.md](https://github.com/acanave/WorkWindow/blob/main/SECURITY.md)
- Privacy notice: [PRIVACY.md](https://github.com/acanave/WorkWindow/blob/main/PRIVACY.md)
- Contribution notes: [CONTRIBUTING.md](https://github.com/acanave/WorkWindow/blob/main/CONTRIBUTING.md)

## Takeaway

WorkWindow shows that a real planning workflow can stay local-first, add cloud sync later, and still feel fast, understandable, and easy to evaluate.
