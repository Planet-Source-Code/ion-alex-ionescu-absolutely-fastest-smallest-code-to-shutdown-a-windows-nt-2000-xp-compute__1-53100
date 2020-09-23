<div align="center">

## Absolutely Fastest, Smallest  Code to Shutdown a Windows NT/2000/XP Computer


</div>

### Description

This code instantly shuts down any NT-based OS, ie Windows NT 4, Windows 2000, XP, Server 2003, Longhorn, etc. (Not 95/98/Me).

I know there's a lot of code on the site that does this, but remember that on NT, things get harder because your process needs the shutdown privilege. Other coders have used Win32 APIs to gain this privilege, but as I have said in my previous articles...the power lies in Native API.

In this unique example, only a single API call is needed to enable the privilege, followed by another API call to instantly terminate the computer. If you compile this application, double-clicking on it will shut down your PC within a second.

Do what you please with it...it might not be very useful most of the time (because it doesn't save any files), but if you ever need a quick shutdown (let's say you just ran a virus), this is as fast as pulling out the power cord.
 
### More Info
 
A closed PC.

Nothing will be saved, instant shutdown.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Ion Alex Ionescu](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ion-alex-ionescu.md)
**Level**          |Beginner
**User Rating**    |5.0 (35 globes from 7 users)
**Compatibility**  |VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[Windows API Call/ Explanation](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/windows-api-call-explanation__1-39.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ion-alex-ionescu-absolutely-fastest-smallest-code-to-shutdown-a-windows-nt-2000-xp-compute__1-53100/archive/master.zip)

### API Declarations

```
RtlAdjustPrivileges
NtShutdownSystem
```


### Source Code

```
' // QuikDown 1.0
' // Written by Alex Ionescu
' // ©Relsoft Technologies 2004
' // COMMENTS: Smallest code to turn off a PC in the fastest way possible on NT.
' // *************
' // APIs
' // *************
' // Undocumented Native API to get Shutdown Privilege
 Public Declare Function RtlAdjustPrivilege& Lib "ntdll" (ByVal Privilege&, ByVal NewValue&, ByVal NewThread&, OldValue&)
' // Native API to Shutdown the System
 Public Declare Function NtShutdownSystem& Lib "ntdll" (ByVal ShutdownAction&)
' // *************
' // Constants
' // *************
' // The Shutdown Privilege
 Public Const SE_SHUTDOWN_PRIVILEGE& = 19
' // The Shutdown Actions
 Public Const SHUTDOWN& = 0
 Public Const RESTART& = 1
 Public Const POWEROFF& = 2
Sub Main()
' // Instantly closes the computer on execution
 RtlAdjustPrivilege SE_SHUTDOWN_PRIVILEGE, 1, 0, 0  ' // Give us Shutdown Privileges
 NtShutdownSystem SHUTDOWN     ' // Take System Down
End Sub
```

