---
title: "Fix mapped drives not showing in Open and Save dialogues in Windows"
tags:
  - fix
  - software
  - windows
  - mapped drives
---

# Problem
User’s mapped drives do not show up as mapped in application Open/Save prompts, even though they show correctly in **File Explorer > This PC**.

# Environment
This issue affects Windows 10 workstations joined to a domain where the user has one or more drives that are automatically mapped via Group Policy Object or NETLOGON script.

# Cause
This problem occurs because UAC treats members of the Administrators group as standard users. Therefore, network shares that are mapped by logon scripts are shared with the standard user access token instead of with the full administrator access token.

# Solution
>[!warning] Caution
Incorrect use of the Windows registry editor may prevent the operating system from functioning properly. Great care should be taken when making changes to a Windows registry. Registry modifications should only be carried-out by persons experienced in the use of the registry editor application.
>
It is recommended that you follow best change management practices and always take a backup of the system registry prior to making modifications in the registry._

To configure the **EnableLinkedConnections** registry value, follow these steps:

1. Click Start, type `regedit` in the Start Search box, and then press ENTER.
2. Locate and then right-click the following registry subkey:
	`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

3. Point to New, and then click **DWORD Value**.
4. Type `EnableLinkedConnections`, and then press ENTER.
5. Right-click **EnableLinkedConnections**, and then click **Modify**.
6. In the Value data box, type `1`, and then click OK.

Exit Registry Editor, and then restart the computer.

---

## Additional Information

https://community.spiceworks.com/how_to/53670-mapped-network-drives-not-showing-in-an-application

https://channel9.msdn.com/Shows/Going+Deep/UAC-What-How-Why#c633305694960000000