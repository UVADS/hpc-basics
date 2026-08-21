---
layout: default
title: Running a batch job
nav_order: 6
permalink: /docs/batch-jobs/
last_modified_date: "2026-08-21 09:20AM"
---

# Running a batch job

A **batch job** is work you submit to the scheduler (**Slurm** on Rivanna/Afton) to run on compute nodes **without** keeping an interactive browser or terminal session open. You write a short script that requests resources (cores, memory, time, partition, account) and lists the commands to run; Slurm queues the job, starts it when resources are free, and writes stdout/stderr to files.

Use batch jobs when interactive Open OnDemand apps are too limited (long runtimes, larger CPU/GPU/memory needs, overnight training, or many sequential/parallel steps). Interactive development still belongs in [Open OnDemand]({{ "/docs/open-ondemand/" | relative_url }}); production-scale runs belong here.

Guide: [Slurm from the CLI (RC Learning Portal)](https://learning.rc.virginia.edu/notes/slurm-from-cli/section2/)

## Software modules (Lmod)

Most central software on Rivanna/Afton is exposed through **Lmod**. Use `module spider`, `module avail`, and `module load` to find and enable compilers, R, Python stacks, and domain packages. In job scripts, load modules **after** the `#SBATCH` lines and **before** your application commands (see next section). Prefer `module purge` first so the job does not inherit modules from your login shell.

Orientation and tutorials:

- [Complete orientation](https://rc.virginia.edu/getting-started/complete-orientation)
- [RC Learning Portal](https://learning.rc.virginia.edu/)

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
| `--mem=` | Memory per node (default unit is MB; you can also use `G`, e.g. `32G`) |
| `--gres=gpu:N` | GPUs (gpu partition); you can also request a type, e.g. `gpu:a6000:1` |
| `-J` / `--job-name=` | Job name |
| `-o` / `-e` | Stdout / stderr files |

General Python job script template:

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

Submit with:

```bash
sbatch myjob.slurm
```

Stage large inputs under `/scratch` or `/project` ([storage]({{ "/docs/services/" | relative_url }})). Replace `YOUR_ALLOCATION` in the examples with your group's account name. Arguments passed to `sbatch` on the command line override matching `#SBATCH` lines in the script.

## Job examples

### Python job

1. Open a terminal on Rivanna/Afton:
   - **Option A (Open OnDemand):** Log in at [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/), then **Clusters** → **HPC Shell Access**.
   - **Option B (SSH):** From a campus network or the [UVA VPN](https://in.virginia.edu/vpn) when off Grounds:

     ```bash
     ssh YOUR_COMPUTING_ID@login.hpc.virginia.edu
     ```

2. Clone the example repository into your home directory:

   ```bash
   cd
   git clone https://github.com/UVADS/jlab-hpc-containers.git
   ```

3. Inspect the job script (uses a system PyTorch container module via Apptainer):

   ```bash
   cd jlab-hpc-containers/
   cat pytorch-example-nocontainer.sh
   ```

   The script looks like this:

   ```bash
   #!/bin/bash
   #SBATCH --account=<your_allocation>     # replace with your allocation
   #SBATCH --partition=gpu
   #SBATCH --gres=gpu:1
   #SBATCH --mem=32G
   #SBATCH --cpus-per-task=4
   #SBATCH --time=00:10:00                 # 10 minutes
   #SBATCH -e slurm-%j.err                 # error file
   #SBATCH -o slurm-%j.out                 # stdout file

   # get example Python script
   curl -o pytorch-example.py https://raw.githubusercontent.com/pytorch/examples/refs/heads/main/mnist/main.py

   module purge
   module load apptainer
   module load pytorch/2.11.0

   apptainer exec --nv $CONTAINERDIR/pytorch-2.11.0.sif python pytorch-example.py
   ```

   The PyTorch container image packages NVIDIA's CUDA stack and a Python interpreter. Edit `--account=` in the script (or pass `-A` to `sbatch`) before submitting.

4. Submit the job. Replace `YOUR_ALLOCATION` with your account. The optional `--gres=gpu:a6000:1` overrides the script's generic `gpu:1` to request a specific GPU type:

   ```bash
   sbatch -A YOUR_ALLOCATION --gres=gpu:a6000:1 pytorch-example-nocontainer.sh
   ```

5. Check job status with `sacct`
6. Check output files `slurm-*.err` and `slurm-*.out`.
   
For a conda env or your own container image, activate that environment (or use `apptainer exec ...`) after loading modules; same pattern as interactive kernels on [JupyterLab]({{ "/docs/open-ondemand/jupyterlab/" | relative_url }}).

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

Full options, partitions, arrays, and advanced patterns: [Slurm from the CLI (learning portal)](https://learning.rc.virginia.edu/notes/slurm-from-cli/section2/) · [RC Training](https://rc.virginia.edu/training)
