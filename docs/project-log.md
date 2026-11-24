Created repo, enabled 2FA.
## 2026-11-23: Phase 1, repo setup and network diagram

**Goal:** Set up the GitHub repo and plan the lab network before building any VMs.

**What I did:**
- Created a GitHub account under a handle, turned on 2FA, and set my commit email to GitHub's private noreply address
- Created the `elk-soc-homelab` repo with a README, `.gitignore` (blocks secrets, VM disks, and ISOs), and this log
- Planned the lab: 3 VMs (elk-siem .10, web-victim .20, kali .30) on a VirtualBox NAT Network, 10.10.10.0/24
- Drew the network diagram in draw.io and added it to the README

**Problems and fixes:**
- Problem: draw.io kept snapping arrows onto the big background boxes.
  Fix: Set the container shapes to `connectable=0` and sent them to the back.
- Problem: The diagram wouldn't show in the README.
  Fix: GitHub file paths are case-sensitive. The README pointed to `diagram.png`, but the file was `Diagram.drawio.png`.
- Problem: README only showed the word "README."
  Fix: The template was never pasted in. Replaced the file's contents with the full README.

**Network+ concepts used:**
- A /24 has 256 addresses and 254 usable hosts (minus the network and broadcast addresses)
- Servers like the SIEM get static IPs because other hosts are configured to send to that fixed address. If DHCP changed it, logs would silently stop arriving and firewall rules would break.
- NAT Network: the VMs can reach the internet through the gateway (10.10.10.1), but nothing outside can connect in
- Reaching Kibana from my PC will need a port-forwarding rule (port address translation) on TCP 5601

**Next time:**
- Update VirtualBox and create the `soc-lab` NAT Network with DHCP off
- Download Ubuntu Server 24.04 LTS and the Kali VirtualBox image
- Add port labels to the diagram arrows
