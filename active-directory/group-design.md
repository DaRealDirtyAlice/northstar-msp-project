# Security Group Design

## Phase 1 groups

| Group | Scope | Purpose |
|---|---|---|
| `GG_HR_Users` | Global / Security | HR department membership |
| `GG_Finance_Users` | Global / Security | Finance department membership |
| `GG_Sales_Users` | Global / Security | Sales department membership |
| `GG_Operations_Users` | Global / Security | Operations department membership |
| `GG_VPN_Users` | Global / Security | Approved remote-access users |
| `GG_Printer_Users` | Global / Security | Users permitted to use the shared printer |
| `GG_HR_Managers` | Global / Security | HR managers |
| `GG_Finance_Managers` | Global / Security | Finance managers |
| `GG_Sales_Managers` | Global / Security | Sales managers |
| `GG_Operations_Managers` | Global / Security | Operations managers |

## Permission model

Use group-based access. Do not grant file permissions directly to named users.

Phase 2 will add domain-local resource groups and use an AGDLP-style flow:

`Account -> Global role group -> Domain Local resource group -> Permission`

Example: `David Chen -> GG_Finance_Users -> DL_FS_Finance_Modify -> NTFS Modify`.

