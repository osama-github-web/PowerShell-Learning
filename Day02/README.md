PowerShell Basics - Day 2
🚀 PowerShell Fundamentals: Basic Commands & Syntax
PowerShell is a powerful scripting language and automation framework built on .NET. This guide covers basic commands, syntax, and best practices to help you get started.

📌 1️⃣ Cmdlets in PowerShell
PowerShell uses cmdlets (pronounced command-lets), which follow a Verb-Noun naming convention.

🔹 What are Cmdlets?
Cmdlets are built-in PowerShell commands that perform specific actions.
Use Get-Command to list all available cmdlets.
🔹 Example: Listing Cmdlets
powershell
Copy
Edit
Get-Command
🔹 Example: Get Help for a Cmdlet
powershell
Copy
Edit
Get-Help Get-Service
Running this script outputs:

pgsql
Copy
Edit
NAME
    Get-Service

SYNTAX
    Get-Service [[-Name] <string[]>] [<CommonParameters>]
🔹 Example: Finding Aliases
powershell
Copy
Edit
Get-Alias -Definition Get-Process
Running this script outputs:

pgsql
Copy
Edit
Alias           Definition
-----           ----------
gps             Get-Process
📌 2️⃣ Variables & Data Types
PowerShell variables are dynamically typed, meaning they can store different types of data without explicit declaration.

🔹 Declaring Variables
powershell
Copy
Edit
$name = "John"
$age = 30
$isAdmin = $true
🔹 Example Script (variables.ps1)
powershell
Copy
Edit
$name = "John"
Write-Host "Hello, $name! You are $age years old."
Running this script outputs:

sql
Copy
Edit
Hello, John! You are 30 years old.
🔹 Checking Data Types
powershell
Copy
Edit
$var1 = "Hello"
$var1.GetType()
Output:

pgsql
Copy
Edit
IsPublic IsSerial Name
-------- -------- -----
True     True     String
🔹 Type Casting
powershell
Copy
Edit
[int]$num = "42"    
[bool]$flag = "True"
[double]$price = "99.99"
📌 3️⃣ Basic Operators
PowerShell supports comparison and logical operators.

🔹 Comparison Operators
Operator	Meaning	Example	Output
-eq	Equal to	5 -eq 5	True
-ne	Not equal to	5 -ne 10	True
-lt	Less than	5 -lt 10	True
-gt	Greater than	5 -gt 3	True
-like	Wildcard match	"Hello" -like "H*"	True
-match	Regex match	"PowerShell" -match "Power"	True
🔹 Example Script (operators.ps1)
powershell
Copy
Edit
$val1 = $true
$val2 = $false

Write-Host ($val1 -and $val2)   # False
Write-Host ($val1 -or $val2)    # True
Write-Host (-not $val1)         # False
Running this script outputs:

graphql
Copy
Edit
False
True
False
📌 4️⃣ Working with Objects
PowerShell treats everything as an object, allowing powerful data manipulation.

🔹 Example: Get a List of Services
powershell
Copy
Edit
Get-Service
🔹 Example: Select Specific Properties
powershell
Copy
Edit
Get-Service | Select-Object Name, Status
Running this script outputs:

sql
Copy
Edit
Name            Status
----            ------
AdobeARMservice Stopped
ALG             Running
Appinfo         Running
🔹 Example: Filter Running Services (services.ps1)
powershell
Copy
Edit
Get-Service | Where-Object { $_.Status -eq "Running" }
Running this script outputs:

sql
Copy
Edit
Status   Name               DisplayName
------   ----               -----------
Running  Spooler            Print Spooler
Running  WSearch            Windows Search
🔹 Example: Convert Object Output to JSON
powershell
Copy
Edit
Get-Service | ConvertTo-Json
Running this script outputs:

json
Copy
Edit
[
  {
    "Status": 4,
    "Name": "Spooler",
    "DisplayName": "Print Spooler"
  },
  {
    "Status": 4,
    "Name": "WSearch",
    "DisplayName": "Windows Search"
  }
]
🎯 Summary
✅ Cmdlets: Use Get-Command, Get-Help, and Get-Alias to explore PowerShell.
✅ Variables: PowerShell supports dynamic typing, but explicit casting is possible.
✅ Operators: -eq, -lt, -gt, -match help in logical conditions.
✅ Objects: Use Select-Object, Where-Object, and Sort-Object for data manipulation.

