---
title: Get KeyWatcher TrueTouch Profile IDs
tags:
  - keywatcher
  - truetouch
  - morse-watchmans
  - mssql
---
# Background
Morse Watchmans KeyWatcher TrueTouch allows key administrators to assign access to keys based on Profiles. Use of this access, and changes to these profiles, is logged and can be audited using inbuilt reports.

For some reason, the TrueTouch software will display the database `ID` of each Profile in the reporting, rather than the actual `ProfileNo` shown in the graphical user interface (GUI) as the "ID". This can make following the audit reports difficult, as auditors and other personnel who routinely review such reports tend to not have access to the database directly.

Because of this, I threw together this simple SQL query that can be used on a KeyWatcher MSSQL database to get the database IDs and their translated IDs shown in the GUI into a single table, which can then be used to cross-reference and audit.

# Query
You can use the below MSSQL query:
```sql
SELECT 
    ID AS 'Database ID',
    ProfileNo AS 'Profile Number',
    Name AS 'Profile Name'
FROM tblProfile
ORDER BY ID
```

# Get the Query File
You can download the above query using the below command:
```PowerShell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/griffeth-barker/public/main/get_keywatcher_profile_ids.sql" -OutFile "$($env:USERPROFILE)\Downloads\get_keywatcher_profile_ids.sql"
```

This is a pretty niche issue, but I hope that someone else find this useful.