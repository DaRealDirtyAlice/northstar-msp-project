# Phase 1 Runbook: AD, DNS, DHCP and Domain Join

## Objective

Build and validate the smallest usable Northstar domain. Start with `DC01` and `WIN11-HR01`; add the other two clients only after the first domain join works.

## Change record

Fill this in during implementation.

| Field | Value |
|---|---|
| Hypervisor | VMware Workstation 17.6.4 |
| Host RAM / usable RAM | TBD |
| VM network type | VMnet3 host-only; VMware DHCP disabled |
| Final subnet | `10.50.10.0/24`; no observed overlap at selection time |
| Windows Server version | Windows Server 2022 Standard Evaluation with Desktop Experience |
| Windows 11 version | TBD |
| Start date | 2026-07-15 |

## Step 1 — Pre-flight

- [x] Confirm virtualization is enabled and the Hypervisor can start one test VM.
- [x] Confirm the proposed subnet does not overlap the host, VPN, or current HomeLab.
- [x] Create an isolated host-only lab network. Do not bridge a lab DHCP server onto the household or office LAN.
- [ ] Take a clean snapshot/checkpoint after OS installation and before role installation.
- [ ] Create an `evidence/phase-1/` folder for sanitized screenshots and command outputs.

### VMware network plan

Create a new custom network (for example `VMnet3`) using `10.50.10.0/24` and host-only mode. Disable VMware's DHCP service on that specific VMnet because `DC01` will provide DHCP. Do not repurpose `VMnet2`; it currently represents `10.10.10.0/24` and may belong to the existing HomeLab.

Initially, keep the Northstar VMs on this isolated network. Internet access is not required to validate AD, DNS and DHCP. Add a controlled second adapter or firewall/NAT design later rather than weakening the lab boundary during bootstrap.

Record the host network using `ipconfig /all`. Capture only the information needed to justify the subnet choice; redact public IPs, adapter IDs and unrelated data.

## Step 2 — Build DC01

- [x] Create the VM and install Windows Server with Desktop Experience.
- [x] Rename the computer to `DC01` and restart.
- [x] Assign `10.50.10.10/24`. Leave the default gateway blank during the isolated Phase 1 build.
- [x] Set preferred DNS to `10.50.10.10`.
- [x] Install AD DS, DNS and DHCP roles.
- [x] Promote the server to a new forest: `corp.northstar.test`.
- [x] Restart and sign in with the domain administrator account.
- [x] Authorize and configure DHCP after confirming network isolation.

Do not record the DSRM password in this repository.

## Step 3 — Validate core services before creating users

Run from `DC01` and save sanitized output:

```powershell
Get-Service ADWS,DNS,DHCPServer
Get-ADDomain
Get-ADForest
Get-DnsServerZone
Get-DhcpServerv4Scope
dcdiag /test:dns
```

Result reported 2026-07-18: required AD and authentication services, Forest/Domain queries, DNS forward/SRV resolution and DHCP configuration checks passed. Final sanitized screenshots remain pending.

## Step 4 — Create OU and groups

- [ ] Follow `ou-structure.md` exactly.
- [ ] Create all groups in `group-design.md`.
- [ ] Create a separate lab admin account for administrative work.
- [ ] Keep the daily user account out of privileged groups.
- [ ] Export the OU and group lists as evidence.

Suggested verification:

```powershell
Get-ADOrganizationalUnit -Filter * | Select-Object Name,DistinguishedName
Get-ADGroup -Filter 'Name -like "GG_*"' | Select-Object Name,GroupScope,GroupCategory
```

## Step 5 — Create 20 virtual users

- [ ] Use `data/users.csv` as the source of truth.
- [ ] Generate a unique username using a documented convention such as first initial + last name.
- [ ] Handle collisions explicitly; do not silently overwrite an account.
- [ ] Set a temporary password interactively, not in CSV.
- [ ] Require password change at next sign-in.
- [ ] Place each user in the correct department OU and group.
- [ ] Add only approved remote workers to `GG_VPN_Users`.
- [ ] Export a user-to-group validation report.

## Step 6 — Configure DHCP

- [x] Create the final IPv4 scope `10.50.10.100–10.50.10.199`.
- [x] Keep static infrastructure ranges outside the dynamic pool; no initial exclusions required.
- [x] Leave gateway option 003 unconfigured during Phase 1 because the host-only network has no router.
- [x] Configure DNS server option 006 to `DC01` (`10.50.10.10`).
- [x] Configure DNS domain option 015 to `corp.northstar.test`.
- [x] Activate the scope.

## Step 7 — Join the first Windows 11 endpoint

- [ ] Create `WIN11-HR01` and connect it to the same lab network.
- [ ] Confirm it receives a DHCP lease.
- [ ] Confirm its DNS server is `DC01`, not a public DNS resolver.
- [ ] Rename and join it to `corp.northstar.test`.
- [ ] Move the computer object to `Northstar/Computers/Workstations`.
- [ ] Sign in with an HR domain user and confirm the password-change workflow.

Client validation commands:

```text
hostname
whoami
ipconfig /all
nslookup dc01.corp.northstar.test
ping dc01
gpupdate /force
gpresult /r
```

## Step 8 — Expand to three clients

- [ ] Repeat for `WIN11-SALES01`.
- [ ] Repeat for `WIN11-REMOTE01`, placing it under `Laptops`.
- [ ] Use a different department account on each endpoint.

## Phase 1 acceptance test

- [ ] All three clients obtain valid DHCP addresses.
- [ ] All three clients list `DC01` as DNS.
- [ ] Forward lookup resolves `DC01` and the domain.
- [ ] Three clients can sign in with domain accounts.
- [ ] Users appear in the correct department OU and group.
- [ ] Computers appear in the correct workstation/laptop OU.
- [ ] A normal user cannot perform domain administration.
- [ ] Evidence contains no passwords, recovery keys, tokens or personal data.
- [ ] Results are recorded in `phase-1-validation.md`.

## Stop conditions

Stop and diagnose before continuing if:

- A client receives `169.254.x.x`.
- A client points to public DNS instead of `DC01`.
- DHCP is visible on the physical LAN.
- Domain join fails but ping by IP succeeds; investigate DNS before rebuilding.
- The first client cannot reliably sign in with a domain account.
