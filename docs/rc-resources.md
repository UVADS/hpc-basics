---
layout: default
title: RC resources
nav_order: 2
permalink: /docs/rc-resources/
last_modified_date: "2026-08-20 04:00PM"
---

# RC resources

[UVA Research Computing (RC)](https://www.rc.virginia.edu/) provides shared HPC and research storage for compute- and data-intensive work. For most data science projects you will use the **Rivanna** and **Afton** clusters (scheduled with Slurm) plus a small set of storage locations.

Official overview: [Computing environments](https://www.rc.virginia.edu/userinfo/computing-environments/)

![UVA Research Computing HPC systems]({{ "/assets/images/hpc.png" | relative_url }})

## Compute

Rivanna and Afton together offer hundreds of CPU nodes (tens of thousands of cores), large per-node memory (roughly hundreds of GB up to ~1.5 TB), and GPU nodes for ML/DL workloads. Jobs run through **Slurm**; interactive work (Jupyter, RStudio, VS Code, Desktop) typically uses the **interactive** partition via the [Open OnDemand web portal](https://ood.hpc.virginia.edu/).

| What you need | Where to start |
| --- | --- |
| CPU / memory-heavy analysis or training | Batch or interactive jobs on Rivanna/Afton |
| GPU work | `gpu` or interactive partitions; see [GPUs on UVA HPC](https://learning.rc.virginia.edu/notes/multigpu-inference/uva-gpus/) |
| Short, interactive sessions (code development, debugging) | Open OnDemand apps (interactive queue; time and resource limits apply) |

**Access is allocation-based.** Compute time is measured in **service units (SUs)** (roughly core-hours; GPUs cost more). Common allocation types:

- **Standard** — free, renews about yearly, normal queue priority
- **Purchased** — paid SUs, higher priority, do not expire
- **Instructional** — free, limited SUs for teaching only, normal queue priority; typically expire about two weeks after the class or training ends

**Only faculty can request an allocation.** They can add students to the allocation as needed.

Details and request paths: [Access to HPC resources](https://www.rc.virginia.edu/userinfo/hpc/access/) · [Pricing](https://www.rc.virginia.edu/userinfo/pricing/) · [Rivanna/Afton FAQ](https://www.rc.virginia.edu/userinfo/faq/rivanna-faq/)

## Storage

Several storage options are available on Rivanna and Afton.

| Location | Quota (typical) | Provisioned | Best for | Caveats |
| --- | --- | --- | --- | --- |
| `/home` | 200 GB, free | Automatic with your HPC account | Scripts, notebooks, light interactive work | Personal only; not ideal for large Slurm I/O |
| `/scratch` | 10 TB, free | Automatic with your HPC account | Active job inputs/outputs (fast parallel FS) | Personal; **no backups**; files unused ~90 days are deleted |
| `/project` | Leased (1 TB+) | Optional; purchased by faculty PI | Shared group data **and** running HPC jobs | Research Project storage; snapshots; paid |
| `/standard` | Leased (1 TB+); PIs may get up to 10 TB free | Optional; requested by faculty PI | Longer-term shared results | Research Standard; slower—**don’t run jobs here** |

Only PIs (faculty) can lease or expand group storage via the [storage request form](https://www.rc.virginia.edu/form/storage/). **Students cannot place storage change requests.**

Full comparison: [HPC storage](https://www.rc.virginia.edu/userinfo/hpc/storage/) · [Storage services](https://www.rc.virginia.edu/services/compute-and-storage/storage)

### Practical pattern

1. Keep code and small configs in `/home` (or a shared `/project` path).
2. Stage large data and write job output to `/scratch` (or `/project` if your group has it).
3. **Copy important data to `/project`, `/standard`, or other storage systems before automatic scratch cleanup deletes them.**

[Globus](https://www.rc.virginia.edu/userinfo/globus/) is the recommended way to move large datasets between your laptop, cloud or lab storage, and HPC-mounted paths (`/home`, `/scratch`, `/project`, `/standard`). Use the managed collection **UVA Standard Security Storage** in the Globus File Manager; for a local machine, install [Globus Connect Personal](https://www.globus.org/globus-connect-personal) first. Guides: [RC data transfer](https://www.rc.virginia.edu/userinfo/storage/data-transfer/) · [Globus tutorial](https://learning.rc.virginia.edu/notes/globus-data-transfer/) · [Globus overview (RC)](https://www.rc.virginia.edu/userinfo/globus/)

Alternatively, you can use familiar command-line tools such as `scp`, `rsync`, `rclone`, or the AWS CLI.

Sensitive / high-security data needs different RC offerings (e.g. Ivy / high-security storage)—see [computing environments](https://www.rc.virginia.edu/userinfo/computing-environments/). **When in doubt, ask Research Computing which option fits your use case.**

## Don't know where to start?

Reach out to the RC team for technical support and consultations. See the [Getting help]({{ "/docs/getting-help/" | relative_url }}) page for details.