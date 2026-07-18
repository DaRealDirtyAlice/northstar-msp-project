# Logical Architecture

## Planned topology

```text
Host PC / VMware host adapter
      |
Northstar Host-only Lab Network - 10.50.10.0/24
      |
      +-- DC01              10.50.10.10  AD DS / DNS / DHCP
      +-- FS01              10.50.10.20  File Services (Phase 2)
      +-- HELPDESK01        10.50.10.30  Ticketing / KB (Phase 3)
      +-- WAZUH01           10.50.10.40  Monitoring (optional reuse)
      +-- WIN11-HR01        DHCP         HR endpoint
      +-- WIN11-SALES01     DHCP         Sales endpoint
      +-- WIN11-REMOTE01    DHCP         Remote-work endpoint
```

## Design decisions

- `corp.northstar.test` is a reserved lab-only namespace.
- Clients must use `DC01` as their DNS server. Public DNS on a domain client can break domain discovery.
- Servers use static addresses; clients use DHCP reservations or dynamic leases.
- Phase 1 uses a single subnet. VLANs are deliberately deferred until support workflows are mature.
- Phase 1 has no default gateway or Internet access. A future `FW01` may use `10.50.10.254` as the gateway after routing is deliberately introduced.
- `DC01` may provide DHCP in the lab but must not compete with a physical-network DHCP server. The VM network must therefore be isolated or correctly scoped.

## Network choice checkpoint

`10.50.10.0/24` is the selected lab subnet. It did not overlap networks observed on 2026-07-15. Recheck whenever the host LAN or VPN changes.
