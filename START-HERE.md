# Start Here

## What is ready

- VMware Workstation 17.6.4 is installed.
- `10.50.10.0/24` does not overlap the networks currently visible on the host.
- The 20-user dataset, OU design, security groups, IP plan, runbook, validation sheet, ticket template and evidence standard are ready.

## First hands-on session

Do only these tasks in the first session:

1. Confirm available RAM and the Windows Server / Windows 11 installation media.
2. In VMware Virtual Network Editor, create a custom host-only network such as `VMnet3` on `10.50.10.0/24`.
3. Disable VMware DHCP for that VMnet; later `DC01` will be the only DHCP server there. Keep the host virtual adapter enabled.
4. Create `DC01` with 2 vCPU, 4 GB RAM and a 60 GB virtual disk.
5. Install Windows Server, rename it to `DC01`, set `10.50.10.10/24` with no default gateway during Phase 1, and take a snapshot before installing roles.
6. Stop and record the session. Do not add AD DS, DNS and DHCP until the base server and isolated network are confirmed stable.

## Evidence to save

- VMware custom network settings with unrelated details cropped
- DC01 VM hardware summary
- `hostname` output after rename
- `ipconfig /all` output containing only the DC01 adapter fields
- Snapshot name and timestamp

Suggested snapshot name: `P1-DC01-BaseOS-BeforeRoles`.

## Do not do yet

- Do not build all seven virtual machines.
- Do not add VLANs or pfSense.
- Do not connect the lab DHCP server to bridged networking.
- Do not create users manually before the OU/group design is deployed.
- Do not publish screenshots until they are sanitized.

After this session, continue from [active-directory/phase-1-runbook.md](active-directory/phase-1-runbook.md), Step 2.
