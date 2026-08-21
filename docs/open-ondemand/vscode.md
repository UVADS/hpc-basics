---
layout: default
title: VSCode (CodeServer)
parent: Open OnDemand interactive apps
nav_order: 3
permalink: /docs/open-ondemand/vscode/
last_modified_date: "2026-08-20 04:20PM"
---

# VSCode (CodeServer)

**Code Server** gives you VS Code in the browser on a Rivanna/Afton **compute node** via Open OnDemand. Files and processes stay on the cluster (they do not sync to your laptop). You can use Git and connect to GitHub for version controlled code management as you would on your local machine.

Links: 
- [Using VS Code on OOD](https://learning.rc.virginia.edu/notes/vscode-intro/using-ood/)
- Portal: [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/)

## Launch

1. Log in at [Open OnDemand](https://ood.hpc.virginia.edu/) with NetBadge.
2. **Interactive Apps** → **Code Server** (name may appear as Code Server / VS Code).
3. Request allocation, time, cores/memory (and GPU if needed), then **Launch**.
4. Connect when the session is ready. When finished, **delete** the session under **My Interactive Sessions**.

## Tips for data science

- Open your project folder on `/home`, `/scratch`, or `/project` from the editor.
- For Python, install the `ms-python` extension and select an interpreter (e.g. miniforge, uv, or a custom env, see RC’s Code Server page).
- Use modules or your own environments on the cluster; you do not need a local VS Code install for this workflow.
