---
layout: default
title: OOD interactive apps
nav_order: 4
has_children: true
permalink: /docs/open-ondemand/
last_modified_date: "2026-08-20 04:10PM"
---

# OOD Interactive Apps

[Open OnDemand (OOD)](https://ood.hpc.virginia.edu/) is RC’s browser portal to Rivanna and Afton. From one dashboard you get a file browser, shell access, job tools, and **Interactive Apps** that run on allocated compute nodes so you can develop and explore without installing HPC clients locally. VPN is not required for OOD (see [Getting access]({{ "/docs/getting-access/" | relative_url }})).

Links: 
- [Interactive apps overview](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/)
- [SSZ login](https://rc.virginia.edu/request-manage/ssz-login)
- Portal: [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/)

Sessions use the **interactive** partition and draw from your group’s allocation (time and resource limits apply). Pick an app under **Interactive Apps**, fill in cores/memory/time (and GPU if needed), then **Launch**.

## Apps for data scientists

| App | Use it for |
| --- | --- |
| [JupyterLab & notebooks]({{ "/docs/open-ondemand/jupyterlab/" | relative_url }}) | Python/R notebooks, interactive analysis, light ML/DL workloads |
| [RStudio Server]({{ "/docs/open-ondemand/rstudio/" | relative_url }}) | R scripting, packages, and interactive data analysis |
| [VSCode (CodeServer)]({{ "/docs/open-ondemand/vscode/" | relative_url }}) | Full VS Code in the browser for editing and debugging on the cluster |
| [Desktop sessions]({{ "/docs/open-ondemand/desktop/" | relative_url }}) | Linux desktop / GUI tools on a compute node (not a login node) |

RC also offers other Interactive Apps (e.g. MATLAB); start from the OOD menu when you need them.

## Non-interactive work

Interactive apps are ideal for development and exploration, but they have time and resource limits. For larger datasets, longer runs, bigger models, more CPUs or memory, or GPUs beyond what the interactive queue allows, submit a [batch job]({{ "/docs/batch-jobs/" | relative_url }}) instead. 

Batch jobs are submitted to the scheduler and execute non-interactively on the requested and allocated resources. 
