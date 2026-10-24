# MARCO

MARCO is a personal homelab network — three machines working together, built and run by one person learning Linux, networking, virtualization, and automation along the way.

## The nodes

| Node | Hardware | Role |
|---|---|---|
| **ROOT** | Raspberry Pi 400 | Management hub: DNS (Pi-hole), dashboard (Homarr), monitoring (Uptime Kuma, Glances), container host (Docker/Portainer), SSH bastion for the rest of the fleet |
| **HOME** | Old desktop (i7-4770, GTX 1060) | Proxmox VE host — VMs, containers, and the Minecraft server |
| **NAS** | Raspberry Pi (Model B Rev 2) | Dedicated file storage — RAID1 mirror, Samba + NFS |

All three talk to each other over a wired LAN, with [Tailscale](https://tailscale.com) for remote access — nothing is ever port-forwarded to the internet.

## Scripts in this repo

| Script | Runs on | What it does |
|---|---|---|
| `marco-status` | ROOT | Full health report — ROOT, HOME, and NAS status, Docker container states, network latency, all in one view |
| `marco-status-short` | ROOT | The quick version — who's online and for how long |
| `marco-menu` | ROOT | An [fzf](https://github.com/junegunn/fzf)-powered launcher menu for everything on ROOT — monitoring, network checks, shells into other nodes, power controls |
| `marco-menu-home` | HOME | Same idea, scoped to Proxmox — containers, VMs, storage pools, backups |
| `marco-menu-nas` | NAS | Same idea again, kept deliberately light for the NAS's limited hardware |
| `marco-kuma-setup` | ROOT | One-time setup script for deploying Uptime Kuma in Docker, including the firewall rule and health check |

## Note on the IP addresses

The IPs in these scripts are placeholder examples (`192.168.1.x`, `100.64.0.x`), not the real addresses — swapped out before publishing. Replace them with your own network's values if you're adapting any of this.

## Why this exists

This repo is both a working toolkit for my own homelab and a record of how it's built — version-controlled instead of living only on the machines it manages.
