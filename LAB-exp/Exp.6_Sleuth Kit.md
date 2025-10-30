# Ex.No.6 — The Sleuth Kit (TSK): Command-Line Digital Forensics

![The Sleuth Kit](https://img.shields.io/badge/The_Sleuth_Kit-4.14.0-blue)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)
![Warning](https://img.shields.io/badge/⚠️-Command_Line-red)

---

## Table of Contents
- [Aim](#aim)
- [Prerequisites & Installation](#prerequisites--installation)
- [Procedure](#procedure)
  - [Step 1: Open Command Prompt & Navigate](#step-1-open-command-prompt--navigate)
  - [Step 2: List Partitions (`mmls`)](#step-2-list-partitions-mmls)
  - [Step 3: Analyze File System (`fsstat`)](#step-3-analyze-file-system-fsstat)
  - [Step 4: List Files and Directories (`fls`)](#step-4-list-files-and-directories-fls)
  - [Step 5: Analyze File Metadata (`istat`)](#step-5-analyze-file-metadata-istat)
  - [Step 6: Recover a File (`icat`)](#step-6-recover-a-file-icat)
  - [Step 7: Create an Event Timeline (`mactime`)](#step-7-create-an-event-timeline-mactime)
- [Result](#result)
- [Notes](#notes)

---

## Aim
To use **The Sleuth Kit (TSK)**, a collection of command-line tools, to analyze a disk image (`4Dell Latitude CPi.E01`), examine its file system, and recover digital evidence.

---

## 🛠️ Prerequisites & Installation

1. **Sleuth Kit Tools:** Download the Windows version of Sleuth Kit (`sleuthkit-4.14.0-win32.zip`) and extract it to a known location (e.g., `C:\Users\sleuthkit-4.14.0-win32`).
2. **Evidence Files:** Download the sample disk image files (`4Dell Latitude CPi.E01` and `4Dell Latitude CPi.E02`) from the Google Drive link provided in the lab manual.
3. **Case Folder:** Create a dedicated folder for your investigation, for example: `C:\Forensics_Lab`. Place the evidence files inside this folder.

---

## Procedure

### Step 1: Open Command Prompt & Navigate
- Open the Command Prompt (`cmd.exe`) **as Administrator**.
- Navigate to the `bin` directory inside your Sleuth Kit folder. This is where all the executable tools (`.exe`) are located.

```bash
C:\Windows\System32> cd C:\Users\sleuthkit-4.14.0-win32\bin
```

<details>
<summary>View Command Prompt 🖥️</summary>
<br>
<p align="center">
  <img width="980" height="96" alt="image" src="https://github.com/user-attachments/assets/bd768c6c-9408-4330-89b9-6e72eaf3f18d" />
</p>
</details>

---

### Step 2: List Partitions (`mmls`)
- Use the `mmls` (list partitions) command to view the partition table of the disk image. This is critical for finding the **offset** (the starting sector) of the partition we want to analyze.
- The path to the image file (`C:\Forensics_Lab\4Dell Latitude CPi.E01`) must be in quotes.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> mmls.exe "C:\Forensics_Lab\4Dell Latitude CPi.E01"
```

📁 **Tip:** The output shows the NTFS / exFAT (0x07) partition (Slot 002) starts at sector 63. This is our offset for the next commands.

<details>
<summary>View mmls Output 🔍</summary>
<br>
<p align="center">
  <img width="980" height="307" alt="image" src="https://github.com/user-attachments/assets/cc4d137d-46f0-48c5-b1ac-ec173981fe23" />
</p>
</details>

---

### Step 3: Analyze File System (`fsstat`)
- Use the `fsstat` (file system statistics) command to get detailed information about the partition.
- We use the `-o 63` flag to specify the partition offset we just found.
- This command prints the output directly to the screen.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> fsstat.exe -o 63 "C:\Forensics_Lab\4Dell Latitude CPi.E01"
```

<details>
<summary>View fsstat Output 📊</summary>
<br>
<p align="center">
  <img width="1252" height="878" alt="image" src="https://github.com/user-attachments/assets/6b50858f-3826-4b00-89b3-bc029125d2bc" />
</p>
</details>

---

### Step 4: List Files and Directories (`fls`)
- Use the `fls` (list files) command to recursively list all files and directories in the partition.
- We use `-r` for recursive and pipe the output `>` to a text file (`file_list.txt`) for easy review and documentation.
- This command will not show any output in the terminal.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> fls.exe -r -o 63 "C:\Forensics_Lab\4Dell Latitude CPi.E01" > C:\Forensics_Lab\file_list.txt
```

📁 **Tip:** You can now open `file_list.txt` in your `C:\Forensics_Lab` folder to see all the files.

<details>
<summary>View file_list.txt Output 📋</summary>
<br>
<p align="center">
  <img width="1354" height="986" alt="Screenshot 2025-10-27 130951" src="https://github.com/user-attachments/assets/e0e98ddb-e7ea-4af8-ad34-2f89a1b14fa0" />
</p>
</details>

---

### Step 5: Analyze File Metadata (`istat`)
- Use the `istat` (inode statistics) command to get detailed metadata about a specific file, such as its MAC (Modified, Accessed, Changed) times.
- From the `file_list.txt`, we identified an interesting file: `Mr. Evil.bmp`.
- Its inode number (the number before the hyphen) is `9871`.
- We redirect the output to a file for our report.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> istat.exe -o 63 "C:\Forensics_Lab\4Dell Latitude CPi.E01" 9871 > C:\Forensics_Lab\metadata_Mr_Evil.txt
```

<details>
<summary>View metadata_Mr_Evil.txt Output 📝</summary>
<br>
<p align="center">
  <img width="986" height="841" alt="image" src="https://github.com/user-attachments/assets/94c3e901-2c15-421e-9213-7a918abbc8fd" />
</p>
</details>

---

### Step 6: Recover a File (`icat`)
- Use the `icat` (inode cat) command to extract the contents of the file using its inode number.
- We use the same inode `9871` and redirect the output, saving it directly as a `.bmp` image.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> icat.exe -o 63 "C:\Forensics_Lab\4Dell Latitude CPi.E01" 9871 > C:\Forensics_Lab\RECOVERED_Mr_Evil.bmp
```

<details>
<summary>View Recovered Image 🖼️</summary>
<br>
<p align="center">
  <img width="1723" height="866" alt="image" src="https://github.com/user-attachments/assets/e25e8de0-c051-467e-9fa0-26e480b466ab" />
</p>
</details>

---

### Step 7: Create an Event Timeline (`mactime`)
- Finally, we create a full timeline of all file activity on the system.
- First, generate a "body file" using `fls`. This file lists MAC times for all files.

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> fls.exe -m / -r -o 63 "C:\Forensics_Lab\4Dell Latitude CPi.E01" > C:\Forensics_Lab\body.txt
```

- Second, use the `mactime.pl` Perl script to sort the body file into a chronological timeline, saved as a `.txt` file (which can also be opened in Excel).

```bash
C:\Users\sleuthkit-4.14.0-win32\bin> mactime.pl -b C:\Forensics_Lab\body.txt > C:\Forensics_Lab\timeline.txt
```

<details>
<summary>View timeline.txt Output ⏳</summary>
<br>
<p align="center">
  <img width="1441" height="92" alt="image" src="https://github.com/user-attachments/assets/8fb02a2a-82ac-44df-b29b-dfd21eb413f1" />
</p>
</details>

---

## ✅ Result
By following these steps, we successfully used The Sleuth Kit to analyze the `4Dell Latitude CPi.E01` disk image. We were able to:

- List the partition table (`mmls`) and identify the correct partition offset (63).
- Analyze the file system metadata (`fsstat`).
- List all files and directories, including deleted ones (`fls`).
- Inspect the detailed metadata of a target file (`istat` on inode 9871).
- Successfully recover the file `Mr. Evil.bmp` (`icat`).
- Generate a full chronological timeline of all file system activity (`mactime`).

All output files and recovered evidence are now stored in the `C:\Forensics_Lab` case folder, ready for reporting.

---

## Notes 📌

⚠️ **Important:** The Sleuth Kit tools are read-only. They do not write to the source image, which preserves the integrity of the evidence.

✅ The Sleuth Kit is the powerful command-line engine that graphical tools like Autopsy are built on. Learning TSK commands gives you a deeper understanding of how forensic analysis works.

💾 Always document your commands and findings. The output files (`.txt`) you create are part of your case notes and final report.

📦 The image offset (`-o 63`) is critical. If you analyze the wrong offset (e.g., the full disk at offset 0), your file system commands will fail.

