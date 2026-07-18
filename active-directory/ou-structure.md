# OU Structure

```text
corp.northstar.test
└── Northstar
    ├── Users
    │   ├── HR
    │   ├── Finance
    │   ├── Sales
    │   └── Operations
    ├── Computers
    │   ├── Workstations
    │   └── Laptops
    ├── Servers
    ├── Disabled Users
    └── Service Accounts
```

## Rules

- User objects go into department OUs.
- Desktop endpoints go into `Workstations`; portable/remote endpoints go into `Laptops`.
- Disabled accounts move to `Disabled Users` after required evidence and group export are saved.
- Administrative work uses a separate named admin account; daily user accounts are not Domain Admins.
- Service accounts are not used for interactive sign-in unless a documented exception exists.

