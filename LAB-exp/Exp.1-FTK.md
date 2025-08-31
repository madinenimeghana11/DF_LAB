# Ex.No.1 — FTK Imager: Forensic Imaging Tool (Detailed Guide)

FTK Imager is a **forensic acquisition tool** widely used to capture both **volatile memory (RAM)** and **non-volatile memory (disk images)** while preserving integrity for digital evidence. Below is the step-by-step expanded process:

---

## 🟢 Volatile Memory (RAM)

RAM is **volatile** – its contents vanish once the computer shuts down. Capturing it **before power-off** is critical to preserve evidence like running processes, passwords, network sessions, and encryption keys.  


---

### Step 1: Run as Administrator
- Right-click the **FTK Imager** icon → select **Run as administrator**.  
- Running as admin ensures the tool has full privileges to read system memory.  
- If not run with elevated privileges, memory capture may fail or be incomplete.  

📌 **Best Practice:** Use a **forensic workstation** or a trusted external device to avoid contaminating the evidence system.
![alt text](image-1.png)



---

### Step 2: Initiate Memory Capture
- Navigate to **File → Capture Memory...**  
- This opens the **Memory Capture Wizard**, specifically designed for live RAM imaging.  
- The wizard prevents accidental overwriting and simplifies capture.  

⚠️ **Why Important?** RAM is constantly changing. Capturing quickly reduces the risk of losing valuable evidence.

![alt text](1b.png)
---

### Step 3: Configure Destination
- **Destination Path:** Always save to an **external drive** (USB, forensic laptop, or network storage).  
- **Filename:** Use descriptive names (e.g., `Case123_RAM_2025-08-31.ad1`).  
- **Include pagefile.sys:** Recommended — it may contain fragments of files or passwords swapped from RAM.  
- **Create AD1 File:** Packages memory dump into AccessData format, easier for analysis.  

📌 **Tip:** Avoid saving directly on the suspect system to prevent evidence contamination.

---

### Step 4: Start Capture
- Click **Capture Memory**.  
- FTK Imager will begin dumping the RAM to the specified location.  
- Progress bar displays percentage completion.  

⚠️ **Note:** The system may slow down during capture. Avoid running other applications.  

![alt text](1c.png)
---

### Step 5: Wait for Completion
- Once completed, FTK Imager generates a **memory dump file**.  
- Verify the file is created in the destination folder.  
- Capture duration depends on system RAM size (e.g., 8GB ≈ few minutes).  

📌 **Outcome:** You now have a **forensically sound RAM dump** ready for analysis (can be examined with tools like Volatility, Rekall, Redline).  

---

## 🔵 Non-Volatile Memory (Disk Image)

Disk imaging preserves a **bit-for-bit copy** of storage media. Unlike regular file copy, it captures **deleted files, hidden data, partitions, and slack space**, crucial for forensic analysis.  

---

### Step 1: Start the Process
- Open FTK Imager → **File → Create Disk Image...**  
- This launches the **Disk Imaging Wizard**.  

📌 **Reason:** Ensures acquisition of all sectors including hidden/deleted data.
![alt text](image.png)

---

### Step 2: Select Source Type
| Source Type     | Description |
|-----------------|-------------|
| **Physical Drive** | Acquires entire disk including partitions, MBR, unallocated space |
| **Logical Drive**  | Captures only a specific partition (e.g., C:) |
| **Image File**     | Converts an existing image to another format |
| **Folder Contents**| Captures only a specific folder |

⚠️ **Best Practice:** Prefer **Physical Drive** to ensure a complete forensic image.
![alt text](1d.png)

---

### Step 3: Select Source Drive
- Attach the suspect drive using a **hardware write-blocker**.  
- Select the correct drive → click **Finish**.  
- Double-check drive details before proceeding to avoid accidental overwriting.  

📌 **Write-blocker Importance:** Prevents modification of evidence media during imaging.

---

### Step 4: Configure Destination
- Click **Add...** → choose **Image Type** and **Destination Path**.  

| Image Type | Description |
|------------|-------------|
| **E01**    | EnCase format (compressed, metadata, widely supported) |
| **Raw (DD)** | Bit-for-bit copy (no compression, universal) |
| **AFF**    | Advanced Forensic Format (open-source, supports compression) |

- Provide **Evidence Info**: Case number, examiner name, description, notes.  
- **Image Fragment Size:** Leave `0` for a single file, or set (e.g., 650MB) for splitting across media.  

⚠️ **Tip:** Keep filenames structured, e.g., `Case123_Disk1_E01`.
![alt text](1f.png)

---

### Step 5: Start Imaging
- Check **Verify images after creation** for automatic hash validation.  
- Click **Start** to begin imaging.  
- Duration depends on drive size and speed (e.g., 500GB HDD ≈ hours).  

📌 **System Impact:** None — imaging reads the suspect disk without altering data.

---

### Step 6: Completion and Hash Verification
- FTK Imager generates **MD5** and **SHA1** hashes for both source and image.  
- ✅ If hashes match → image integrity is confirmed.  
- ❌ If mismatch → repeat acquisition or investigate hardware issues.  

📌 **Why Hashing Matters?** Ensures **chain-of-custody** and proves evidence has not been altered.
<img src="https://github.com/user-attachments/assets/739045f1-11bc-474a-9343-2e9aa19ec376" alt="Disk Imaging Animation" width="600">

---

## 📌 Notes
- ⚠ Always use a **write-blocker** when imaging storage devices.  
- ✅ Always document evidence details and acquisition steps.  
- 🔑 Hash verification is mandatory for admissibility in court.  
- 📂 For large drives, fragmentation helps in storage and transfer.  

---

## 📚 References
- [FTK Imager Official Website](https://accessdata.com/product-download/ftk-imager-version-4-5)  
- Carrier, B. (2005). *File System Forensic Analysis*.  
- Casey, E. (2011). *Digital Evidence and Computer Crime*.  

