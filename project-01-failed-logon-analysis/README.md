# Project 01 – Failed Logon Analysis (Windows)

## Objective
Establish a baseline of failed logon activity on a Windows system.

## Environment
- Windows 11
- Windows Event Viewer

## Investigation
Security Event Logs were reviewed filtering for Event ID 4625.

## Observations
- Event ID 4625 was generated after a manual failed login attempt using a Windows Hello PIN.
- The authentication attempt did not map to a specific user account.
- The event was logged under the SYSTEM context using svchost.exe.
- Logon Type observed: 2 (Interactive).
- Source network address was localhost (127.0.0.1).

## Baseline conclusion
The failed logon event was triggered by an incorrect Windows Hello PIN attempt.
Due to the authentication method, the event did not resolve to a specific user account
and was logged under the SYSTEM context. This behavior is consistent with normal
Windows authentication mechanisms and does not indicate malicious activity.

## Next steps
- Complete baseline observation
- Automate event extraction with PowerShell
- Simulate controlled failed logon attempts

## Part 2 – PowerShell extraction
- Used Get-WinEvent with FilterHashtable to extract Event ID 4625 from the Security log.
- Converted events to XML and extracted key fields (TargetUserName, LogonType, IpAddress, ProcessName).
- Confirmed interactive failed logons (LogonType 2) with localhost source (127.0.0.1) during testing.
