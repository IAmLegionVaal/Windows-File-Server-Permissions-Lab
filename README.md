# Windows File Server Permissions Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![Windows Server](https://img.shields.io/badge/Platform-Windows%20Server-0078D4)
![SMB](https://img.shields.io/badge/Service-SMB%20File%20Sharing-2F6FED)

A completed Windows Server lab in which I configured SMB file shares, Active Directory security groups, share permissions and NTFS permissions for controlled departmental access.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real share names, users, groups, hostnames, addresses and credentials have been generalized.

## Objectives completed

- Created departmental and shared-data folders
- Published folders as SMB shares
- Created Active Directory security groups for access control
- Assigned read, modify and administrative permissions
- Tested inheritance and explicit permissions
- Validated allowed and denied access from domain clients
- Reviewed effective access and resolved permission conflicts
- Documented troubleshooting findings

## Implementation summary

1. Created a structured folder layout on the Windows file server.
2. Created role-based Active Directory security groups.
3. Added test users to the appropriate groups.
4. Configured share permissions at the SMB layer.
5. Configured NTFS permissions using least-privilege access.
6. Preserved or disabled inheritance where appropriate.
7. Connected to the shares from domain-joined endpoints.
8. Tested read, create, modify and delete actions with different users.
9. Reviewed effective permissions when results differed from expectations.

## Example validation commands

```powershell
Get-SmbShare
Get-SmbShareAccess -Name "<share-name>"
Get-Acl "D:\Shares\<folder-name>" | Format-List
Get-SmbSession
Get-SmbOpenFile
```

```cmd
net use
whoami /groups
```

## Outcome

The file server successfully provided different access levels according to Active Directory group membership. Authorized users could access and modify the intended data, while users outside the approved groups were denied or limited to read-only access as designed.

## Findings

- Effective access was determined by the combination of share and NTFS permissions; the most restrictive result controlled network access.
- Role-based security groups were easier to manage and audit than assigning permissions directly to individual users.
- Group-membership changes sometimes required a sign-out or refreshed logon token before the new access level became visible.
- Explicit deny entries were powerful but increased troubleshooting complexity and were avoided unless a clear requirement existed.
- Inheritance simplified administration when the folder structure matched the access model, but sensitive subfolders required deliberate inheritance changes.
- Testing both successful and denied actions was necessary to prove that the permission model worked securely.

## Skills demonstrated

- Windows file server administration
- SMB share configuration
- NTFS permission design
- Active Directory security groups
- Least-privilege access control
- Effective-permission troubleshooting
- Domain client access testing
- Technical documentation

## Security notes

- No production data or credentials are included.
- All identities and paths shown in examples are placeholders.
- The lab was completed in a controlled non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
