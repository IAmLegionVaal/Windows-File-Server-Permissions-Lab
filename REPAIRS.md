# Repairs and Remediation Performed

The completed file-server lab included corrective work where access tests did not initially match the intended permission design.

## Repairs completed

- Corrected users placed in the wrong Active Directory security groups.
- Corrected mismatched SMB share and NTFS permission levels.
- Repaired inherited permissions on folders that required a different access boundary.
- Removed unnecessary direct user assignments in favour of role-based groups.
- Refreshed user logon tokens after group-membership changes.
- Reconnected client share mappings after permission corrections.
- Re-tested read, create, modify and delete operations with approved and denied users.

## Validation after repair

```powershell
Get-SmbShareAccess -Name "<share-name>"
Get-Acl "D:\Shares\<folder-name>" | Format-List
```

```cmd
whoami /groups
net use
```

The repaired permission model was validated from both the server and domain-client sides.

**This was tested by me to be working. User experience may vary.**
