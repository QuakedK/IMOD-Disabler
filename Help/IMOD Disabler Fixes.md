# IMOD Disabler Fixes

# #1 Microsoft's Vulnerable Driver Blocklist
**How to disable** 
1. Simple open CMD as admin and paste the following ↓
```
reg add "HKLM\SYSTEM\CurrentControlSet\Control\CI\Config" /v "VulnerableDriverBlocklistEnable" /t REG_DWORD /d "0" /f
```
2. Restart your pc!

**How to enable** 
1. Simple open CMD as admin and paste the following ↓
```
reg add "HKLM\SYSTEM\CurrentControlSet\Control\CI\Config" /v "VulnerableDriverBlocklistEnable" /t REG_DWORD /d "1" /f
```
2. Restart your pc!

> [!NOTE]
> Downloading the manual version of IMOD Disabler, allows you to disable/enable Microsoft's Vulnerable Driver Blocklist.

# #2 Memory Integrity/Core Isolation
**How to disable** 
1. Simple open CMD as admin and paste the following ↓
```
reg add "HKLM\System\CurrentControlSet\Control\DeviceGuard\Scenarios\HypervisorEnforcedCodeIntegrity" /v "Enabled" /t REG_DWORD /d "0" /f
```
2. Restart your pc!

**How to enable** 
1. Simple open CMD as admin and paste the following ↓
```
reg add "HKLM\System\CurrentControlSet\Control\DeviceGuard\Scenarios\HypervisorEnforcedCodeIntegrity" /v "Enabled" /t REG_DWORD /d "1" /f
```
2. Restart your pc!

> [!NOTE]
> Downloading the manual version of IMOD Disabler, allows you to disable/enable Memory Integrity/Core Isolation by enabling Microsoft's Vulnerable Driver Blocklist from the menu.

# #3 Remove IMOD Script From Startup
**How to delete the Run Registry Key Version**
1. Simple open CMD as admin and paste the following ↓
```
reg delete "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v "IMOD Disabler" /f
```

**How to delete the TaskVersion** 
1. Simple open CMD as admin and paste the following ↓
```
schtasks /delete /tn "IMOD Disabler" /f
```

# #4 BSOD On Startup
Assuming the you ran the Automatic version of IMOD Disabler or used the manual version and selected the add **Run Registry Key**, you may experience BSOD's on startup. 
The running theory has something to do with the registry startup key. Possibly related to the timing of when the XHCI-IMOD-Interval.ps1 script is executed. And the obvious way to avoid this is simply by choosing the task scheduler startup version.
Or by Manual excuting the IMOD Script yourself. 

However assuming you currently stuck in a BSOD loop, refer to the following steps:

**Easy Method**
1. Simply restart your pc.
2. After you logged in, quickly Open Task Manager and disable the powershell.exe

**Upon your next start XHCI-IMOD-Interval.ps1 won't open**

**Method 2** 
1. Restart 3 times or hold shift while restarting.
2. It should put you in advanced recovery.
3. Once there, click Troubleshoot.
4. Click Advanced Options then Startup Settings, then click restart.
5. While in Startup settings click 4 Enable Safe Mode.
6. When booted in,  Open Task Manager and disable the powershell.exe

Videos: -> [How to get to advanced recovery](https://www.tiktok.com/t/ZTYoQrNHx/) & [How to enable safe boot](https://www.youtube.com/watch?v=jtJCkG_lZtI) 

> [!NOTE]
> Running the manual version and selecting **Add IMOD Script to Startup (Task Scheduler)** should fix the BSOD'ing upon startup.
>
> **Want to add it easily?**
> 1. Simple open CMD as admin and paste the following ↓
```
schtasks /create /tn "IMOD Disabler" /tr "Powershell -NoProfile -ExecutionPolicy Bypass -File \"C:\IMOD Disabler Tools\IMOD Scripts\XHCI-IMOD-Interval.ps1\"" /sc onstart /ru system /rl highest /f 
```
2. Restart your pc!

