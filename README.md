# LocalSplash Connectivity Diagnostics

Standalone Windows connectivity utility. It checks public ICMP connectivity through `1.1.1.1`, internal connectivity through `172.83.90.32`, and the computer's current public IP address.

## Run on Windows

1. Open the private GitHub repository and choose **Code > Download ZIP**.
2. Extract the ZIP to a permanent folder, for example:

   ```
   C:\LocalSplash\ConnectivityDiagnostics
   ```

3. Open **Windows PowerShell**. Administrator access is not normally required.
4. Change to the extracted folder:

   ```powershell
   cd C:\LocalSplash\ConnectivityDiagnostics
   ```

5. Start the utility:

   ```powershell
   powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\ConnectivityDiagnostics.ps1
   ```

6. Leave the console open while troubleshooting.

   - Press **C** to copy a sanitized diagnostic report, then paste it into the IT request.
   - Press **Q** to quit.

For a single check that exits automatically:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\ConnectivityDiagnostics.ps1 -Once -NonInteractive
```

If Windows blocks the downloaded files, right-click the ZIP before extracting it, choose **Properties**, select **Unblock**, and apply the change. Company security policy takes precedence; do not weaken machine-wide execution policy.

## Configuration

Edit `config.json` to change targets, intervals, or timeouts. Defaults:

- Public target: `1.1.1.1`
- Internal target: `172.83.90.32`
- Check interval: 10 seconds
- Ping timeout: 2 seconds

## Automated tests

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\tests\Run-Tests.ps1
```

## PowerShell 7 / Linux development

PowerShell 7 uses `pwsh`. This is the development and automated-test path, not the primary Windows-user path:

```
pwsh -NoProfile -File ./ConnectivityDiagnostics.ps1
