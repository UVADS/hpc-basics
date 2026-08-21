---
layout: default
title: Getting access
nav_order: 3
permalink: /docs/getting-access/
last_modified_date: "2026-08-20 08:15PM"
---

# Getting access

To use Rivanna and Afton you need a **UVA computing ID** (NetBadge) and membership in a faculty PI's **allocation** (managed with Grouper). Students and most trainees do **not** request allocations themselves.

Official guides: [Get access to HPC resources](https://rc.virginia.edu/getting-started/get-access-high-performance-computing-resources) · [SSZ login](https://rc.virginia.edu/request-manage/ssz-login) · [Request & Manage](https://rc.virginia.edu/request-manage)

## What you need

| Role | What to do |
| --- | --- |
| **Student / collaborator** | Ask your PI or course instructor to add you to their Grouper group for the allocation. Then log in (below). |
| **Faculty PI** | Create a Grouper group, add yourself as a member, request a standard (or other) allocation, then add students. |

Eligibility notes (from RC):

- Faculty may serve as PI and request HPC allocations and storage.
- Graduate and undergraduate students **cannot** request allocations; their advisor or instructor must.
- Sponsored-account users can join a faculty Grouper group but cannot request RC services as PI.

Allocation types (standard, purchased, instructional) are summarized under [RC resources]({{ "/docs/rc-resources/" | relative_url }}). Full request details: [Get access to HPC resources](https://rc.virginia.edu/getting-started/get-access-high-performance-computing-resources) · forms on [Request & Manage](https://rc.virginia.edu/request-manage).

### Grouper (for PIs)

Access is controlled by **Grouper** group membership ([group management](https://in.virginia.edu/group-management); VPN required to use the portal). For a new group, note that it will be used for Rivanna/Afton access, add yourself as a member, then submit the allocation request (for example the [standard allocation form](https://forms.rc.virginia.edu/form/allocation-standard/)).

## How to log in

Use your **UVA computing ID**. Passwords are your NetBadge / Eservices credentials (reset via [ITS](https://virginia.service-now.com/) if needed).

| Method | URL / host | VPN off Grounds? | Best for |
| --- | --- | --- | --- |
| **Open OnDemand** (recommended start) | [ood.hpc.virginia.edu](https://ood.hpc.virginia.edu/) | **No** | Browser apps, files, shell, job tools |
| **SSH** | `login.hpc.virginia.edu` | **Yes** | Terminal / scripting |
| **FastX** (remote desktop) | [fastx.hpc.virginia.edu](https://fastx.hpc.virginia.edu/) | **Yes** | Linux desktop / some GUI apps |

Example SSH:

```bash
ssh YOUR_COMPUTING_ID@login.hpc.virginia.edu
```

Off Grounds, use the [UVA VPN](https://in.virginia.edu/vpn) (prefer **More Secure Network** when available) for SSH and FastX. Open OnDemand does not require VPN.

More detail: [SSZ login](https://rc.virginia.edu/request-manage/ssz-login) · [Open OnDemand apps]({{ "/docs/open-ondemand/" | relative_url }}) · [Interactive apps (learning portal)](https://learning.rc.virginia.edu/notes/hpc-intro/interactive_apps/interactive/)

## After you can log in

1. Confirm you can open [Open OnDemand](https://ood.hpc.virginia.edu/) and see your home directory.
2. Learn where data should live ([RC resources: Storage]({{ "/docs/rc-resources/" | relative_url }})).
3. Try an interactive app ([Open OnDemand interactive apps]({{ "/docs/open-ondemand/" | relative_url }})) or a simple batch job later.

If login fails after you were added to a group, wait a short time for membership to propagate, confirm your NetBadge password, then contact [RC support]({{ "/docs/getting-help/" | relative_url }}) with your computing ID and PI/group name.
