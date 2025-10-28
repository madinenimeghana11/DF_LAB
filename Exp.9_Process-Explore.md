
# Ex.No.9 — Using Procmon to Identify Suspicious Processes

## Aim
To monitor and identify suspicious process activities in a Windows system using **Procmon (Process Monitor)**.

## Introduction
**Procmon** is a Windows Sysinternals tool used for real-time monitoring of system activities such as file system access, registry modifications, process creation, and network operations. It helps in malware analysis, troubleshooting system issues, and detecting unauthorized or malicious behaviors by providing detailed logs of all running processes.

## Required Software
- **Procmon (Process Monitor)** — Download from the official Microsoft Sysinternals site:  
  🔗 [https://learn.microsoft.com/en-us/sysinternals/downloads/procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon)
- **Windows OS** (any version with administrative privileges)

## Procedure
1. **Download and extract Procmon** from the Microsoft Sysinternals site.
2. **Run Procmon as Administrator** to allow system-level monitoring.
   <p align="center">
       <img width="1414" height="872" alt="image" src="https://github.com/user-attachments/assets/c3f5f5f2-cdfa-4bd5-9653-9d6d0632d95e" />
   </p>
4. **Start Capture** by clicking the **Capture Events (Ctrl + E)** icon.
  <p align="center">
    <img width="1420" height="868" alt="image" src="https://github.com/user-attachments/assets/1a8a45ea-ba33-4727-9071-545076b9a2b7" />
  </p>

6. Perform normal or suspicious operations (e.g., run unknown executables).
7. **Stop Capture** after sufficient data collection.
8. **Filter the events**:
   - Go to *Filter → Filter...*
   - Add filters such as:
     - `Process Name contains suspicious.exe`
     - `Operation contains WriteFile` or `CreateProcess`

 <p align="center">
      <img width="948" height="647" alt="image" src="https://github.com/user-attachments/assets/357d7583-bcc5-4380-a340-3cfd831074bc" />
 </p>
 
9. Analyze the logs:
   - Check **Process Tree** to view parent-child relationships.
   - Identify unexpected registry changes or file access.
   - Export suspicious events to CSV for reporting.
   
<p align="center">
    <img width="1621" height="1200" alt="image" src="https://github.com/user-attachments/assets/cc4cf7ee-889a-4195-a373-b6bcdb3e26bb" />

</p>

10. **Close Procmon** and review captured data for persistence or injection signs.

## Result
Successfully used **Procmon** to capture and analyze system process activities. Suspicious processes performing abnormal registry modifications, file writes, or network access were identified, providing insights into potential malicious behavior.

