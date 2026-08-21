---
layout: default
title: Tools
nav_order: 6
permalink: /docs/tools/
last_modified_date: "2026-08-20 04:45PM"
---

# Tools

Software and integrations that help data scientists move data, manage environments, and work with Rivanna and Afton, from your laptop or on the cluster.

## Rivanna MCP

[UVADS/rivanna-mcp](https://github.com/UVADS/rivanna-mcp) is a local **MCP (Model Context Protocol)** server that connects AI-enabled IDEs (Cursor, Claude Code, and similar) to Afton/Rivanna over SSH. In plain language, you can ask your assistant about cluster status, your jobs and allocations, storage use, modules, and job submission, without pasting Slurm output by hand.

It is aimed at day-to-day HPC workflow support from your laptop: monitor and manage jobs, inspect resources, and draft or submit batch work through the assistant. Setup, client config, and the full tool list live in the [rivanna-mcp README](https://github.com/UVADS/rivanna-mcp).

## Globus file transfer

[Globus](https://learning.rc.virginia.edu/notes/globus-data-transfer/) is RC's recommended service for moving **large** datasets to and from HPC storage (`/home`, `/scratch`, `/project`, `/standard`), lab machines, cloud, and other institutions. Use the managed collection **UVA Standard Security Storage** in the Globus File Manager; install [Globus Connect Personal](https://www.globus.org/globus-connect-personal) on a laptop first. For highly sensitive / Ivy data, use the high-security transfer path described in that tutorial and on [Ivy/Rio](https://rc.virginia.edu/services/compute-and-storage/ivyrio).

Also useful: [Globus tutorial](https://learning.rc.virginia.edu/notes/globus-data-transfer/) · storage notes on [RC resources]({{ "/docs/rc-resources/" | relative_url }})

## Apptainer containers

[Apptainer](https://learning.rc.virginia.edu/notes/containers-for-hpc/using/) (formerly Singularity) runs portable container images on the HPC system. Useful when you need a fixed ML/science stack, Docker-based images, or the same environment in notebooks and batch jobs. RC also ships many apps as container modules. For wiring containers into JupyterLab kernels, see [Custom JupyterLab kernels]({{ "/docs/open-ondemand/jupyterlab/" | relative_url }}) and [UVADS/jlab-hpc-containers](https://github.com/UVADS/jlab-hpc-containers).

## Workflow managers

For multi-step, reproducible pipelines (ETL, bioinformatics, ML training stages, etc.), prefer a **workflow manager** over a pile of ad-hoc scripts. On UVA HPC these typically submit work through Slurm and can use modules or containers for each step.

Common options for data science and analytics (tutorials and comparisons): **[UVADS/workflow-basics](https://github.com/UVADS/workflow-basics)** / [site](https://uvads.github.io/workflow-basics/)

| Tool | Notes |
| --- | --- |
| **Nextflow** | Scalable pipelines; works well with Slurm and Apptainer/Conda on Rivanna/Afton |
| **Snakemake** | Make-like Python workflows; strong for file-oriented pipelines |
| **Cromwell / WDL** | Workflow Description Language; common in genomics-style pipelines |
| **Prefect** | Python-native orchestration for data/analytics workflows |

Interactive browser apps (JupyterLab, RStudio, Code Server, Desktop) are covered under [Open OnDemand]({{ "/docs/open-ondemand/" | relative_url }}).
