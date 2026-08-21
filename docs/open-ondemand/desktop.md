---
layout: default
title: Desktop sessions
parent: Open OnDemand interactive apps
nav_order: 4
permalink: /docs/open-ondemand/desktop/
last_modified_date: "2026-08-20 04:20PM"
---

# Desktop sessions

The Open OnDemand **Desktop** app starts a full Linux desktop on a **compute node** with the resources you request (including GPUs when needed). Prefer this for compute-heavy GUI work instead of FastX on a login/frontend node.

Guides: [Interactive apps overview](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/) · Portal: [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/)

## Launch

1. Log in at [Open OnDemand](https://ood.hpc.virginia.edu/) with NetBadge.
2. **Interactive Apps** → **Desktop**.
3. Choose allocation, time, cores/memory, and GPU if your GUI app needs one.
4. **Launch**, then connect to the desktop when the job starts.

## When to use it

- GUI tools that are not available as a dedicated OOD app
- Visualization or interactive software that needs a desktop environment on allocated hardware

**Do not** use the Desktop session as a place to submit other Slurm jobs; treat it as your interactive compute environment. For light file browsing or editing on a frontend, FastX may be enough but heavy work belongs on Desktop or a dedicated app ([interactive apps overview](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/)).

Delete the session under **My Interactive Sessions** when you are done so the allocation is released.
