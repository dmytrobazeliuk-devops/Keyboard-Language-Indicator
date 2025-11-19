# Standard Install Return Codes for Microsoft Store

## Standard Windows Installer Return Codes

### Installation cancelled by user
**EXE return code value:** `1602`
**Description:** ERROR_INSTALL_USEREXIT - The installation was cancelled by the user.

### Application already exists
**EXE return code value:** `1605`
**Description:** ERROR_INSTALL_ALREADY_RUNNING - The application is already installed. This indicates that the product is already installed on the device.

### Installation already in progress
**EXE return code value:** `1618`
**Description:** ERROR_INSTALL_ALREADY_RUNNING - Another installation is already in progress. The user needs to complete the current installation before proceeding with this install.

### Disk space is full
**EXE return code value:** `1603`
**Description:** ERROR_INSTALL_FAILURE - Fatal error during installation. This can occur when disk space is insufficient. Alternatively, you can use `112` (ERROR_DISK_FULL) for more specific disk space errors.

### Reboot required
**EXE return code value:** `3010`
**Description:** ERROR_SUCCESS_REBOOT_REQUIRED - A restart is required to complete the installation. The installation was successful, but the system needs to be rebooted.

### Network failure
**EXE return code value:** `1603`
**Description:** ERROR_INSTALL_FAILURE - General installation failure. For network-specific errors, you can also use:
- `1203` - ERROR_EXTENDED_ERROR (Network path not found)
- `53` - ERROR_BAD_NETPATH (Network path not found)
- `64` - ERROR_NETNAME_DELETED (Network name deleted)
- `2250` - ERROR_INSTALL_NETWORK_FAILURE (Network failure during installation)

### Package rejected during installation
**EXE return code value:** `1625`
**Description:** ERROR_INSTALL_PACKAGE_REJECTED - The installation package was rejected due to a security policy enabled on the device. This typically occurs when Windows Defender or Group Policy blocks the installation.

### Installation successful
**EXE return code value:** `0`
**Description:** ERROR_SUCCESS - Installation has been successful.

### Miscellaneous install failure scenarios

**General installation failure:**
- **EXE return code value:** `1603`
- **Description:** ERROR_INSTALL_FAILURE - Fatal error during installation
- **Documentation:** https://docs.microsoft.com/windows/win32/msi/error-codes

**Invalid installation package:**
- **EXE return code value:** `1601`
- **Description:** ERROR_INSTALL_SERVICE_FAILURE - Invalid handle or service failure

**Installation suspended:**
- **EXE return code value:** `1604`
- **Description:** ERROR_INSTALL_SUSPEND - Installation suspended

**Access denied:**
- **EXE return code value:** `5`
- **Description:** ERROR_ACCESS_DENIED - Access is denied (insufficient permissions)

**File not found:**
- **EXE return code value:** `2`
- **Description:** ERROR_FILE_NOT_FOUND - The system cannot find the file specified

**Invalid parameter:**
- **EXE return code value:** `87`
- **Description:** ERROR_INVALID_PARAMETER - The parameter is incorrect

## Additional Common Return Codes

| Code | Description | Scenario |
|------|-------------|----------|
| 0 | Success | Installation completed successfully |
| 1602 | User exit | User cancelled the installation |
| 1603 | Fatal error | General installation failure |
| 1605 | Already installed | Product already exists |
| 1618 | Already running | Another installation in progress |
| 1625 | Package rejected | Security policy blocked installation |
| 3010 | Reboot required | Installation successful, reboot needed |
| 112 | Disk full | Insufficient disk space |
| 5 | Access denied | Insufficient permissions |
| 2 | File not found | Required file missing |
| 87 | Invalid parameter | Invalid command line parameter |

## Notes for Microsoft Store Submission

- **MSIX packages** typically use different return codes than traditional MSI installers
- For **MSIX**, the Store handles most installation scenarios automatically
- If providing an **EXE installer** (not MSIX), use the codes above
- Always return `0` for successful installation
- Return non-zero codes only for actual failures
- The Store will interpret these codes and display appropriate messages to users

## References

- Windows Installer Error Codes: https://docs.microsoft.com/windows/win32/msi/error-codes
- MSIX Packaging: https://docs.microsoft.com/windows/msix/
- Microsoft Store Policies: https://docs.microsoft.com/microsoft-store/policies

