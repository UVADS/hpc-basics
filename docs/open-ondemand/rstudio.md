---
layout: default
title: RStudio Server
parent: OOD interactive apps
nav_order: 2
permalink: /docs/open-ondemand/rstudio/
last_modified_date: "2026-08-20 04:20PM"
---

# RStudio Server

RStudio Server on Rivanna/Afton is an Open OnDemand interactive app: a full RStudio IDE in the browser on a **compute node**.

Links: 
- [Interactive apps overview](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/)
- Portal: [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/)

## Launch

1. Log in at [Open OnDemand](https://ood.hpc.virginia.edu/) with NetBadge.
2. **Interactive Apps** → **RStudio Server**.
3. Fill in the form (allocation, partition/time, cores/memory; select an R version).
   > **Note:** Request only the cores, memory, GPUs, and wall time you need. Smaller, shorter jobs usually start sooner because the scheduler can fit them into free capacity more easily.
4. Click **Launch**. When ready, click **Connect to RStudio Server**.

You can navigate the cluster filesystem from within RStudio. If the browser disconnects, reopen the session from **My Interactive Sessions** while the job is still running. Delete the session when done to free resources.

## Tips for data science

- Install packages as you would locally, subject to cluster network and module constraints (outbound access is limited; some sites are whitelisted; see RC’s RStudio page).
- Put large data under `/scratch` or `/project` ([storage overview]({{ "/docs/services/" | relative_url }})).
- For long, non-interactive R jobs, prefer a [batch job]({{ "/docs/batch-jobs/" | relative_url }}) over an open RStudio session.

## Example scripts & codes

*Placeholder: example R scripts and projects will be added here.*
