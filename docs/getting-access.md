---
layout: default
title: Getting access
nav_order: 3
permalink: /docs/getting-access/
last_modified_date: "2026-08-20 03:55PM"
---

# Getting access

To use Rivanna and Afton you need a **UVA computing ID** (NetBadge) and membership in a faculty PI’s **allocation** (managed with Grouper). Students and most trainees do **not** request allocations themselves.

Official guides: [Access to HPC resources](https://www.rc.virginia.edu/userinfo/hpc/access/) · [Logging in](https://www.rc.virginia.edu/userinfo/hpc/login/)

## What you need

| Role | What to do |
| --- | --- |
| **Student / collaborator** | Ask your PI or course instructor to add you to their Grouper group for the allocation. Then log in (below). |
| **Faculty PI** | Create a Grouper group, add yourself as a member, request a standard (or other) allocation, then add students. |

Eligibility notes (from RC):

- Faculty may serve as PI and request HPC allocations and storage.
- Graduate and undergraduate students **cannot** request allocations—their advisor or instructor must.
- Sponsored-account users can join a faculty Grouper group but cannot request RC services as PI.

Allocation types (standard, purchased, instructional) are summarized under [RC resources]({{ "/docs/rc-resources/" | relative_url }}). Full request details: [Access to HPC resources](https://www.rc.virginia.edu/userinfo/hpc/access/).

### Grouper (for PIs)

Access is controlled by **Grouper** group membership ([Grouper / group management](https://virginia.service-now.com/its/?id=itsweb_kb_article&sys_id=dbe787581b9e3514a4fb33b61a4bcb37); VPN required to use the portal). For a new group, note that it will be used for Rivanna/Afton access, add yourself as a member, then submit the allocation request. ITS has short tutorials on creating groups and adding members (linked from the RC access page).

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

More detail: [Logging in](https://www.rc.virginia.edu/userinfo/hpc/login/) · [Open OnDemand](https://www.rc.virginia.edu/userinfo/hpc/ood/)

## After you can log in

1. Confirm you can open [Open OnDemand](https://ood.hpc.virginia.edu/) and see your home directory.
2. Learn where data should live ([RC resources — Storage]({{ "/docs/rc-resources/" | relative_url }})).
3. Try an interactive app ([Open OnDemand interactive apps]({{ "/docs/open-ondemand/" | relative_url }})) or a simple batch job later.

If login fails after you were added to a group, wait a short time for membership to propagate, confirm your NetBadge password, then contact [RC support]({{ "/docs/getting-help/" | relative_url }}) with your computing ID and PI/group name.
