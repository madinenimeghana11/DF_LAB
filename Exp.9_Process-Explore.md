
# Ex.No.9 — Using Process Explorer to Identify Suspicious Processes

![Process Explorer](https://img.shields.io/badge/Tool-Process%20Explorer-green)
![Platform](https://img.shields.io/badge/Platform-Windows-orange)
![Type](https://img.shields.io/badge/Analysis-Process%20Monitoring-blue)

**📚 Course / Lab:** Digital Forensics Lab  
**🔢 Experiment No.:** 9  
**📝 Title:** Use Process Explorer to Identify Suspicious Processes

---

## 📑 Table of Contents

- [Ex.No.9 — Using Process Explorer to Identify Suspicious Processes](#exno9--using-process-explorer-to-identify-suspicious-processes)
  - [📑 Table of Contents](#-table-of-contents)
  - [🎯 Aim](#-aim)
  - [🛠️ Requirements](#️-requirements)
  - [📝 Description](#-description)
  - [📋 Step-by-Step Procedure](#-step-by-step-procedure)
    - [Step 1: Download and Setup Process Explorer](#step-1-download-and-setup-process-explorer)
    - [Step 2: Understand the Interface](#step-2-understand-the-interface)
    - [Step 3: Identify Suspicious Processes](#step-3-identify-suspicious-processes)
    - [Step 4: Analyze Process Behavior](#step-4-analyze-process-behavior)
    - [Step 5: Verify Process Legitimacy](#step-5-verify-process-legitimacy)
    - [Step 6: Take Appropriate Action](#step-6-take-appropriate-action)
    - [Step 7: Example Observation](#step-7-example-observation)
  - [✅ Result](#-result)
  - [📝 Notes](#-notes)

---

## 🎯 Aim
To use Microsoft Sysinternals **Process Explorer** to monitor system activities and identify any **suspicious or malicious processes** running on a Windows computer.

---

## 🛠️ Requirements

- **💻 Windows operating system**
- **🌐 Internet connection**
- **🔧 Process Explorer** (from Microsoft Sysinternals)
- **🛡️ Optional:** Antivirus software (e.g., Windows Defender, Malwarebytes)

---

## 📝 Description
Process Explorer is a part of the **Microsoft Sysinternals Suite**. It is a powerful tool used to view detailed information about system processes. It helps investigators and administrators analyze active processes, detect suspicious behavior, monitor CPU and memory usage, and verify process authenticity using digital signatures.

---

## 📋 Step-by-Step Procedure

### Step 1: Download and Setup Process Explorer

**🎯 Purpose:** Obtain and configure Process Explorer for system process analysis.

**📋 Instructions:**

1. **📥 Go to the official Microsoft Sysinternals website:**
   🔗 [https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)

2. **⬇️ Click **Download Process Explorer**.**

3. **📦 Extract the downloaded ZIP file to a folder.**

4. **👨‍💼 Right-click `procexp64.exe` (for 64-bit) or `procexp.exe` (for 32-bit) → select **Run as Administrator**.**

---

### Step 2: Understand the Interface

**🎯 Purpose:** Familiarize yourself with Process Explorer's interface and color coding system.

**📋 Instructions:**

1. **🌳 The main window displays all running processes in a **hierarchical tree view**.**

2. **📊 Each process shows details such as **PID**, **CPU usage**, **memory usage**, and **company name**.**

3. **🎨 Color codes represent process states:**
   - 🟩 **Green** — Newly started processes
   - 🟥 **Red** — Terminated processes
   - 🟦 **Light Blue** — Processes running under the current user
   - 🟪 **Pink** — Suspended processes

<details>
<summary>🖥️ View Process Explorer Interface</summary>
<br>
<p align="center">
  <img width="700" alt="Process Explorer main interface" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/20813074f7e55b479108660a16f276f69e56ad41/images/9.1.jpeg" />
</p>
</details>

---

### Step 3: Identify Suspicious Processes

**🎯 Purpose:** Learn to recognize potentially malicious processes through various indicators.

**📋 Instructions:**

1. **🔍 Look for **unfamiliar or oddly named processes** (e.g., `xkdjeo.exe`, `randomname123.exe`).**

2. **🏢 Check the **Company Name** and **Description**:**
   - Legitimate software usually shows known publishers like *Microsoft*, *Intel*, or *Adobe*.

3. **🖱️ Right-click the process → **Properties** → go to the **Image** tab.**

4. **📁 Verify the **Path** of the executable file:**
   - ✅ **Safe:** `C:\Windows\System32\`
   - ⚠️ **Suspicious:** `C:\Users\<User>\AppData\Temp\` or `Downloads\`

5. **🔐 Check for **Digital Signature**:**
   - Valid signature = trusted developer
   - No signature or invalid = possibly malicious

<details>
<summary>🔍 View Process Properties Analysis</summary>
<br>
<p align="center">
  <img width="600" alt="Process properties and digital signature verification" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/326db74a3770e2ba22207f5a48b737f17307f683/images/9.10.jpeg" />
</p>
</details>

---

### Step 4: Analyze Process Behavior

**🎯 Purpose:** Monitor resource usage and network activity to detect malicious behavior.

**📋 Instructions:**

1. **📊 Observe **CPU**, **Memory**, and **I/O usage** columns.**

2. **⚠️ If a small or unknown process consumes **excessive CPU or memory**, it may be malicious.**

3. **🌐 Right-click the process → **Properties** → go to the **TCP/IP tab**.**
   - Check if it communicates with **unknown external IP addresses**.

4. **🔧 Examine **Handles** and **DLLs** tabs for suspicious loaded files or libraries.**

<details>
<summary>📈 View Resource Usage Analysis</summary>
<br>
<p align="center">
  <img width="700" alt="Process resource usage and network connections" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/326db74a3770e2ba22207f5a48b737f17307f683/images/9.4.jpeg" />
</p>
</details>

---

### Step 5: Verify Process Legitimacy

**🎯 Purpose:** Use external resources to confirm whether a process is legitimate or malicious.

**📋 Instructions:**

1. **🔍 Search the process name on Google.**
   Example: `svchost.exe` vs `svhost.exe` (one letter missing — suspicious).

2. **🛡️ Visit 🔗 [https://www.virustotal.com](https://www.virustotal.com)**
   - Upload the process file or search its name to verify if it's reported as malware.

3. **📚 Cross-check with **ProcessLibrary.com** or official vendor websites for authenticity.**

<details>
<summary>🔍 View VirusTotal Verification</summary>
<br>
<p align="center">
  <img width="700" alt="VirusTotal malware verification results" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/326db74a3770e2ba22207f5a48b737f17307f683/images/9.6.jpeg" />
</p>
</details>

---

### Step 6: Take Appropriate Action

**🎯 Purpose:** Execute proper procedures to handle identified malicious processes.

**📋 Instructions:**

1. **🚨 If the process is confirmed malicious:**
   - Right-click the process → **Kill Process** to stop it.
   - Delete the corresponding executable file from its path.

2. **🤔 If unsure:**
   - Right-click → **Suspend Process** to stop it temporarily for investigation.

3. **🧹 After removal:**
   - Run a **Full System Scan** using Windows Defender or Malwarebytes to ensure no remnants remain.

<details>
<summary>⚡ View Process Termination</summary>
<br>
<p align="center">
  <img width="600" alt="Process termination and cleanup procedures" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/326db74a3770e2ba22207f5a48b737f17307f683/images/9.8.jpeg" />
</p>
</details>

---

### Step 7: Example Observation

**🎯 Purpose:** Practical example of identifying and handling a malicious process.

**📋 Case Study:**

**🔍 Discovery:** You find `faangpath_simple_template.pdf` consuming 70% CPU.

**📊 Analysis Results:**
- **📁 Path:** `C:\Users\Admin\AppData\Temp\faangpath_simple_template.pdf`
- **🔐 Digital Signature:** None
- **🏢 Company Name:** Unknown
- **🌐 Network Activity:** Shows connections to unknown IPs in the TCP/IP tab
- **🛡️ Online Check:** VirusTotal confirms it as a **known trojan**

**⚡ Action Taken:**
1. Suspended → Killed → Deleted file → Performed full antivirus scan

<details>
<summary>🚨 View Malicious Process Detection</summary>
<br>
<p align="center">
  <img width="700" alt="Example of detected malicious process analysis" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/326db74a3770e2ba22207f5a48b737f17307f683/images/9.9.jpeg" />
</p>
</details>

---

## ✅ Result

Using Process Explorer, suspicious processes were successfully identified by examining their **CPU usage**, **path**, **digital signature**, and **network activity**. Confirmed malicious processes were terminated and removed to maintain system integrity.

🎯 **Key Achievements:**
- ✅ Successfully downloaded and configured Process Explorer with administrative privileges
- ✅ Mastered the interface and color-coding system for process identification
- ✅ Identified suspicious processes through path analysis and resource monitoring
- ✅ Verified process legitimacy using digital signatures and online databases
- ✅ Successfully terminated malicious processes and performed system cleanup
- ✅ Implemented best practices for ongoing system security monitoring

**📊 Investigation Summary:**
- 🔍 **Detection Method:** Resource usage analysis, path verification, signature checking
- 🛡️ **Verification Tools:** VirusTotal, ProcessLibrary, digital signature validation
- ⚡ **Response Actions:** Process suspension, termination, file deletion, system scanning
- 📋 **Documentation:** Complete forensic analysis workflow established

---

## 📝 Notes

⚠️ **Administrator Privileges:** Always run Process Explorer as administrator to access all system processes and perform administrative actions.

🔍 **False Positives:** Some legitimate processes may appear suspicious due to unusual names or locations. Always verify through multiple sources before taking action.

🛡️ **System Safety:** Before terminating critical system processes, ensure they are not essential for system operation. Terminating system processes can cause system instability.

💡 **Best Practices:**
- Regular monitoring of running processes
- Maintain updated antivirus software
- Monitor unusual CPU/memory usage patterns
- Verify digital signatures for unknown processes
- Keep system and security software updated

🔧 **Advanced Features:**
- **Process Tree View** - Shows parent-child relationships
- **System Information** - Displays overall system performance
- **Handle Monitoring** - Tracks file and registry access
- **DLL Analysis** - Examines loaded libraries

⚡ **Real-Time Monitoring:**
- Set up automatic refresh for real-time process monitoring
- Use filters to focus on specific process types
- Monitor network connections for suspicious activity
- Track process startup and termination events

---

**🔗 Related Tools:**
- [Autoruns](https://docs.microsoft.com/en-us/sysinternals/downloads/autoruns) - Startup program analysis
- [TCPView](https://docs.microsoft.com/en-us/sysinternals/downloads/tcpview) - Network connection monitoring
- [ProcMon](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) - Real-time file system and registry monitoring

---

*📅 Last Updated: October 2025*
*👨‍💻 Author: Digital Forensics Lab*
