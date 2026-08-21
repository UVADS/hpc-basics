---
layout: default
title: JupyterLab & notebooks
parent: OOD interactive apps
nav_order: 1
permalink: /docs/open-ondemand/jupyterlab/
last_modified_date: "2026-08-20 04:30PM"
---

# JupyterLab & notebooks

JupyterLab on Rivanna/Afton runs as an Open OnDemand interactive app on a **compute node** (not a login node). Use it for notebooks, exploratory analysis, and light ML/DL work with optional GPUs.

Links: 
- [Interactive apps overview](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/)
- Portal: [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/)

## Launch

1. Log in at [Open OnDemand](https://ood.hpc.virginia.edu/) with NetBadge.
2. **Interactive Apps** → **JupyterLab**.
3. Fill in the form (allocation, partition/time, cores/memory, working directory; request a GPU if needed).
4. Click **Launch**. When the job starts, click **Connect to Jupyter**.

Keep the OOD **My Interactive Sessions** tab available so you can reconnect or delete the session when finished (that releases resources).

## Tips for data science

- Prefer `/scratch` or `/project` for large inputs/outputs; keep notebooks and small scripts in `/home` or a project path ([storage overview]({{ "/docs/services/" | relative_url }})).
- Prefer a **custom kernel** when you need a fixed package stack (see below). Don’t rely only on the default OOD Python.
- Interactive sessions have time and resource limits; use [batch jobs]({{ "/docs/batch-jobs/" | relative_url }}) for long training runs.

## Custom JupyterLab kernels

A **kernel** is the language runtime JupyterLab attaches to a notebook. The default kernels are convenient, but research projects usually need a **custom kernel** backed by an isolated environment so your packages, versions, and CUDA/ML stacks stay reproducible and don’t clash with other work.

Two common patterns on Rivanna/Afton:

| Backing environment | Idea |
| --- | --- |
| **Conda / Mamba / Miniforge env** | Create an env with `ipykernel`, then register it so it appears in JupyterLab’s kernel picker. |
| **Apptainer container** | Run the notebook’s Python from a `.sif` image (also needs `ipykernel` inside). Same image can later back batch jobs for consistency. |

In both cases Jupyter stores a small **kernel spec** under `~/.local/share/jupyter/kernels/` that tells OOD how to start that environment. Create or register kernels from an SSH shell, FastX, or OOD **HPC Shell Access** and not from a terminal *inside* an already-running JupyterLab session (RC notes that can put the kernel in the wrong place).

Step-by-step for container-backed kernels: [Custom Jupyter Kernel (RC Learning Portal)](https://learning.rc.virginia.edu/notes/containers-for-hpc/using/#custom-jupyter-kernel).

For containerized kernels aimed at data science / ML on UVA HPC, including `jkrollout` / `jkrollout2` helpers and examples that reuse the same image for interactive and batch work, see **[UVADS/jlab-hpc-containers](https://github.com/UVADS/jlab-hpc-containers)**.

## Example scripts & codes

*Placeholder: example notebooks and scripts will be added here.*

