# 🛠 PowerShell Learning Path

## ✅ Phase 1: PowerShell Fundamentals (Beginner)

### 🔹 1. Understanding PowerShell Basics

### What is PowerShell? (CLI vs. Scripting)
PowerShell is a command-line shell and scripting language developed by Microsoft, primarily used for system administration, automation, and configuration management. It is built on **.NET**, meaning it can interact with Windows system components, Active Directory, the registry, and even REST APIs.

#### PowerShell as a CLI (Command-Line Interface)
- Similar to Command Prompt (`cmd.exe`), PowerShell allows running individual commands interactively.
- Commands are called **cmdlets** (pronounced "command-lets"), which follow the verb-noun format.
- Example:
  ```powershell
  Get-Process
  ```
  This lists all running processes on the system.

#### PowerShell as a Scripting Language
- PowerShell can execute multiple commands in a structured script file (`.ps1`).
- It supports variables, loops, functions, and error handling.
- Example script (`example.ps1`):
  ```powershell
  $name = "John"
  Write-Host "Hello, $name!"
  ```
  Running this script outputs:
  ```
  Hello, John!
  ```

---

### 🔹 Installing & Updating PowerShell

#### Checking Your Current PowerShell Version
Run the following command in PowerShell:
```powershell
$PSVersionTable.PSVersion
```
Example output:
```
Major  Minor  Build  Revision
-----  -----  -----  --------
7      3      0      0
```
- **PowerShell 5.1** comes pre-installed on Windows 10/11.
- **PowerShell 7 (Core)** is the latest cross-platform version.

#### Installing PowerShell on Windows
1. **Via Microsoft Store**
   - Open **Microsoft Store** and search for **PowerShell**.
   - Install the latest version.

2. **Via Winget (Windows Package Manager)**
   Open PowerShell as Administrator and run:
   ```powershell
   winget install --id Microsoft.Powershell --source winget
   ```

3. **Via MSI Installer**
   - Download from: [PowerShell GitHub Releases](https://github.com/PowerShell/PowerShell/releases)
   - Run the MSI installer and follow the instructions.

#### Installing PowerShell on Linux/macOS
- Install PowerShell using package managers:
  ```bash
  sudo apt-get install -y powershell     # Ubuntu/Debian
  sudo yum install -y powershell         # CentOS/RHEL
  brew install --cask powershell         # macOS (Homebrew)
  ```

#### Updating PowerShell
To update to the latest version, use:
```powershell
winget upgrade --id Microsoft.PowerShell
```

---

### 🔹 PowerShell Console vs. PowerShell ISE vs. VS Code

#### 1️⃣ PowerShell Console (CLI)
- The standard command-line interface where you run PowerShell commands interactively.
- To open it:
  - **Windows**: Press `Win + R`, type `powershell`, and hit Enter.
  - **Linux/macOS**: Run `pwsh` in a terminal.

**Example:**
```powershell
Get-Service
```
This lists all running services.

#### 2️⃣ PowerShell ISE (Integrated Scripting Environment)
- A built-in editor for writing, testing, and debugging PowerShell scripts.
- Provides syntax highlighting, auto-completion, and debugging tools.
- To open it:
  - Press `Win + R`, type `powershell_ise`, and hit Enter.

**Example in PowerShell ISE:**  
```powershell
for ($i=1; $i -le 5; $i++) {
    Write-Host "Iteration: $i"
}
```
This script prints numbers 1 to 5.

#### 3️⃣ Visual Studio Code (VS Code)
- A more advanced code editor with extensions for PowerShell development.
- Provides better debugging, Git integration, and cross-platform support.
- To use PowerShell in VS Code:
  - Install **VS Code** from [code.visualstudio.com](https://code.visualstudio.com/)
  - Install the **PowerShell Extension** from the VS Code marketplace.

**Example using VS Code Terminal:**
```powershell
Get-Process | Where-Object { $_.CPU -gt 10 }
```
This filters processes using more than 10% CPU.

---

### 🔹 Execution Policies (Security Restrictions in PowerShell)

PowerShell has execution policies to protect against running malicious scripts. These policies control whether scripts can be executed.

#### Checking the Current Execution Policy
Run:
```powershell
Get-ExecutionPolicy
```
Example output:
```
Restricted
```
This means script execution is **disabled** by default.

#### Types of Execution Policies
---------------------------------------------------------------------------------------------------
| Policy Name   | Description                                                                     |
|---------------|---------------------------------------------------------------------------------|
| `Restricted`  | **(Default)** Only interactive commands allowed, scripts cannot run.            |
| `AllSigned`   | Only scripts signed by a trusted publisher can run.                             |
| `RemoteSigned`| Locally created scripts run, but downloaded scripts require a digital signature.|
| `Unrestricted`| All scripts can run, but a warning appears for downloaded scripts.              |
| `Bypass`      | No restrictions, any script runs without warning.                               |
---------------------------------------------------------------------------------------------------

#### Changing the Execution Policy
To allow scripts to run, use:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
- `-Scope CurrentUser`: Applies only to the logged-in user.
- `-Scope MachinePolicy`: Applies system-wide (requires admin).

#### Running a Script Temporarily Bypassing Execution Policy
```powershell
powershell -ExecutionPolicy Bypass -File .\myscript.ps1
```
This runs the script without changing system-wide policy.

#### Example: Creating and Running a PowerShell Script
1. Open **Notepad** and type:
   ```powershell
   Write-Host "Hello, PowerShell!"
   ```
2. Save the file as `hello.ps1`.
3. Try to run it:
   ```powershell
   .\hello.ps1
   ```
4. If you get an execution policy error, change the policy:
   ```powershell
   Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```
5. Run the script again, and you should see:
   ```
   Hello, PowerShell!
   ```

---

## 🎯 Summary
✅ **PowerShell** is both a CLI and a scripting language, great for automation.  
✅ **Install & Update** PowerShell using Microsoft Store, `winget`, or package managers.  
✅ **Use PowerShell ISE or VS Code** for better scripting and debugging.  
✅ **Execution Policies** control script security; `RemoteSigned` is a safe setting.  

Would you like to add more sections or hands-on exercises? 🚀