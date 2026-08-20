---
layout: default
title: Running a batch job
nav_order: 5
permalink: /docs/batch-jobs/
last_modified_date: "2026-08-20 04:50PM"
---

# Running a batch job

A **batch job** is work you submit to the scheduler (**Slurm** on Rivanna/Afton) to run on compute nodes **without** keeping an interactive browser or terminal session open. You write a short script that requests resources (cores, memory, time, partition, account) and lists the commands to run; Slurm queues the job, starts it when resources are free, and writes stdout/stderr to files.

Use batch jobs when interactive Open OnDemand apps are too limited (long runtimes, larger CPU/GPU/memory needs, overnight training, or many sequential/parallel steps). Interactive development still belongs in [Open OnDemand]({{ "/docs/open-ondemand/" | relative_url }}); production-scale runs belong here.

Official guide: [Slurm Job Manager (RC)](https://www.rc.virginia.edu/userinfo/hpc/slurm/)

## Software modules (Lmod)

Most central software on Rivanna/Afton is exposed through **Lmod**. Use `module spider`, `module avail`, and `module load` to find and enable compilers, R, Python stacks, and domain packages. In job scripts, load modules **after** the `#SBATCH` lines and **before** your application commands (see next section). Prefer `module purge` first so the job does not inherit modules from your login shell.

Guide: [Software modules](https://www.rc.virginia.edu/userinfo/hpc/software/modules/)

## Job scripts

A Slurm job script is a bash script that starts with `#!/bin/bash`, then a preamble of `#SBATCH` directives that define resource requests (nodes, CPU cores, memory, specialty hardware such as GPUs, and a time limit), then the commands to execute.

Typical directives:

| Directive | Purpose |
| --- | --- |
| `-A` / `--account=` | Allocation (Grouper account) to charge |
| `-p` / `--partition=` | Queue (e.g. `standard`, `parallel`, `gpu`) |
| `-t` / `--time=` | Wall-clock limit |
| `-n` / `--ntasks=` | Number of tasks |
| `-c` / `--cpus-per-task=` | Cores per task |
| `--mem=` | Memory (MB) per node |
| `--gres=gpu:N` | GPUs (gpu partition) |
| `-J` / `--job-name=` | Job name |
| `-o` / `-e` | Stdout / stderr files |

Submit with:

```bash
sbatch myjob.slurm
```

Stage large inputs under `/scratch` or `/project` ([storage]({{ "/docs/rc-resources/" | relative_url }})). Replace `YOUR_ALLOCATION` in the examples with your group’s account name.

## Job examples

### Python job

```bash
#!/bin/bash
#SBATCH -A YOUR_ALLOCATION
#SBATCH -p standard
#SBATCH -t 01:00:00
#SBATCH -n 1
#SBATCH -c 4
#SBATCH --mem=16000
#SBATCH -J py-example
#SBATCH -o py-example-%A.out
#SBATCH -e py-example-%A.err

module purge
module load miniforge

python myscript.py
```

For a conda env or container-backed run, activate that environment (or `apptainer exec …`) after loading modules—same pattern as interactive kernels on [JupyterLab]({{ "/docs/open-ondemand/jupyterlab/" | relative_url }}).

### Rscript job

```bash
#!/bin/bash
#SBATCH -A YOUR_ALLOCATION
#SBATCH -p standard
#SBATCH -t 01:00:00
#SBATCH -n 1
#SBATCH -c 4
#SBATCH --mem=16000
#SBATCH -J r-example
#SBATCH -o r-example-%A.out
#SBATCH -e r-example-%A.err

module purge
module load goolf R

Rscript myscript.R
```

Check available R versions with `module spider R` before submitting.

## Checking jobs

| Command | Use |
| --- | --- |
| `squeue -u $USER` | Your jobs in the queue / running |
| `scancel <jobid>` | Cancel a job |
| `sacct -j <jobid>` | Accounting / exit status after it finishes |
| `seff <jobid>` | Efficiency summary (CPU/memory use) |
| `scontrol show job <jobid>` | Detailed job state |

Watch the `-o` / `-e` files for application output and errors.

## Slurm references

Most common commands: `sbatch`, `squeue`, `scancel`, `sacct`, `seff`, `sinfo` (partition/node overview), `scontrol`.

Full options, partitions, arrays, and advanced patterns: [Slurm Job Manager — UVA Research Computing](https://www.rc.virginia.edu/userinfo/hpc/slurm/) · [Slurm from the CLI (learning portal)](https://learning.rc.virginia.edu/notes/slurm-from-cli/section2/)
