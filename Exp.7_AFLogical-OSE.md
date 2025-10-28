
# Ex.No.7 — Use AFLogical OSE to Extract Data from Android Devices

![AFLogical OSE](https://img.shields.io/badge/Tool-AFLogical%20OSE-green)
![Platform](https://img.shields.io/badge/Platform-Android-orange)
![Type](https://img.shields.io/badge/Analysis-Logical%20Extraction-blue)

**📚 Course / Lab:** Digital Forensics Lab  
**🔢 Experiment No.:** 7  
**📝 Title:** Use AFLogical OSE to Extract Data from an Android Device

---

## 📑 Table of Contents

- [📝 Description](#-description)
- [📋 Step-by-Step Process](#-step-by-step-process)
  - [Step 1: Prepare Your Environment](#step-1-prepare-your-environment)
  - [Step 2: Connect the Android Device to Your Computer](#step-2-connect-the-android-device-to-your-computer)
  - [Step 3: Extract Data Using AFLogical OSE](#step-3-extract-data-using-aflogical-ose)
  - [Step 4: Transfer Extracted Data to Your Computer](#step-4-transfer-extracted-data-to-your-computer)
  - [Step 5: Analyze the Extracted Data](#step-5-analyze-the-extracted-data)
  - [Step 6: Clean Up](#step-6-clean-up)
- [✅ Result](#-result)
- [📝 Notes](#-notes)

---

## 📝 Description
**AFLogical OSE (Open Source Edition)** is a tool designed for logical data extraction from Android devices. As part of the Open Source Android Forensics project, it collects non-file system data like **contacts**, **messages (SMS/MMS)**, and **call logs** without needing root access.

---

## 📋 Step-by-Step Process

### Step 1: Prepare Your Environment

**🎯 Purpose:** Set up the required tools and environment for Android data extraction.

**📋 Instructions:**

1. **📥 Download AFLogical OSE:**
   - Visit the AFLogical OSE GitHub page and download the latest release, or clone the repository using Git.

2. **☕ Install Java:**
   - AFLogical OSE requires Java to run. Ensure Java is installed on your machine.

3. **🔧 Install Android Debug Bridge (ADB):**
   - Download **ADB** (a command-line tool for device communication) from the Android Developer's website.
   - Install it on your system and **add it to your system's PATH environment variable** for easy access from the command line.

4. **📱 Enable USB Debugging on the Android Device:**
   - Go to **Settings > About Phone** and tap **Build Number seven times** to enable Developer Options.
   - Go to **Settings > Developer Options** and enable **USB Debugging**.

<details>
<summary>📱 View Developer Options Setup</summary>
<br>
<p align="center">
  <img width="600" alt="Android Developer Options setup" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.1.png" />
</p>
</details>

<details>
<summary>⚙️ View USB Debugging Configuration</summary>
<br>
<p align="center">
  <img width="600" alt="USB Debugging enabled" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.3.png" />
</p>
</details>

---

### Step 2: Connect the Android Device to Your Computer

**🎯 Purpose:** Establish a stable connection between the Android device and computer.

**📋 Instructions:**

1. **🔌 Connect via USB:**
   - Use a USB cable to connect the Android device to your computer.

2. **🔍 Verify ADB Connection:**
   - Open Command Prompt/Terminal and run the following command:
   ```bash
   adb devices
   ```
   - **✅ Verification:** The device should be listed, confirming that the ADB connection is ready.

<details>
<summary>💻 View ADB Connection Verification</summary>
<br>
<p align="center">
  <img width="700" alt="ADB devices command output" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/7bc2c6c9cc6dd5cdd9401ae3781aa66e70193dde/images/7.13.jpeg" />
</p>
</details>

---

### Step 3: Extract Data Using AFLogical OSE

**🎯 Purpose:** Install and execute AFLogical OSE on the target Android device.

**📋 Instructions:**

1. **📦 Push the APK to the Android Device:**
   - Navigate to the AFLogical OSE directory in your terminal.
   - Run the command to install the AFLogical OSE APK on the device:
   ```bash
   adb install aflogical.apk
   ```

<details>
<summary>📱 View APK Installation Process</summary>
<br>
<p align="center">
  <img width="700" alt="AFLogical APK installation" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.7.png" />
</p>
</details>

2. **🚀 Launch the AFLogical OSE App on the Device:**
   - On the Android device, open the newly installed AFLogical app.

3. **✅ Select and Start Data Extraction:**
   - Select the desired data types (e.g., contacts, SMS, MMS, call logs) from the app's options.
   - The app will start the extraction process, storing the data in **.csv files** on the device's storage, typically in a directory named `aflogical`.

<details>
<summary>📊 View Data Selection Interface</summary>
<br>
<p align="center">
  <img width="400" alt="AFLogical data selection interface" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.12.jpeg" />
</p>
</details>

<details>
<summary>⚡ View Extraction Process</summary>
<br>
<p align="center">
  <img width="400" alt="Data extraction in progress" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.11.jpeg" />
</p>
</details>

---

### Step 4: Transfer Extracted Data to Your Computer

**🎯 Purpose:** Transfer the extracted data from the Android device to your computer for analysis.

**📋 Instructions:**

1. **📥 Use ADB to Pull Data:**
   - After extraction is complete, transfer the collected data files from the Android device to your computer using the `adb pull` command:
   ```bash
   adb pull /sdcard/aflogical /path/to/destination
   ```
   - **📝 Note:** Replace `/path/to/destination` with the desired save location on your computer.

<details>
<summary>📁 View Data Transfer Process</summary>
<br>
<p align="center">
  <img width="700" alt="ADB pull command execution" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.8.png" />
</p>
</details>

2. **🔍 Verify the Data:**
   - Navigate to the destination directory and check the `.csv` files to ensure all required data has been successfully transferred.

---

### Step 5: Analyze the Extracted Data

**🎯 Purpose:** Examine and analyze the extracted data for forensic evidence.

**📋 Instructions:**

1. **📊 Open the CSV Files:**
   - Use applications like **Excel**, **Google Sheets**, or a text editor to open and analyze the `.csv` files containing the extracted logical data.

2. **📝 Review and Document:**
   - Carefully review the data for any relevant evidence or information.
   - Document all findings and prepare a comprehensive report.

<details>
<summary>📈 View Data Analysis</summary>
<br>
<p align="center">
  <img width="700" alt="CSV data analysis in spreadsheet" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/de2d7c56c138c87d4745d2dbaf512dc4e2beaedc/images/7.9.png" />
</p>
</details>

---

### Step 6: Clean Up

**🎯 Purpose:** Properly clean up the environment and remove forensic tools from the device.

**📋 Instructions:**

1. **🗑️ Uninstall AFLogical OSE:**
   - Once data extraction is complete and verified, safely uninstall the app from the Android device:
   ```bash
   adb uninstall com.viaforensics.android.aflogical
   ```

2. **🔌 Disconnect the Device:**
   - Safely disconnect the Android device from your computer.

**🎯 Summary:** By following these steps, you successfully perform a logical extraction on an Android device using AFLogical OSE, a valuable technique in digital forensic investigations.

---

## ✅ Result

The experiment using AFLogical OSE was successfully performed. The tool efficiently extracted logical data such as contacts, messages, and media files from the mobile device, demonstrating its usefulness in mobile forensic data acquisition.

🎯 **Key Achievements:**
- ✅ Successfully configured ADB environment and established device communication
- ✅ Installed and deployed AFLogical OSE APK to the target Android device
- ✅ Performed logical extraction of key user data (contacts, SMS/MMS, call logs)
- ✅ Successfully transferred extracted data from device to computer for analysis
- ✅ Analyzed extracted CSV files containing forensic evidence
- ✅ Completed proper cleanup and device disconnection procedures

**📊 Data Extraction Summary:**
- 👥 **Contacts:** Complete contact database with names, numbers, and details
- 💬 **SMS/MMS:** Text and multimedia message history with timestamps
- 📞 **Call Logs:** Incoming, outgoing, and missed call records
- 📅 **Metadata:** Device information and extraction timestamps
- 📁 **File Format:** CSV files for easy analysis and documentation

---

## 📝 Notes

⚠️ **Legal Compliance:** Always ensure you have proper authorization before performing forensic extraction on any device. This tool should only be used for legitimate forensic investigations, academic research, or on devices you own.

🔒 **Data Security:** Handle extracted data with appropriate security measures. Forensic data may contain sensitive personal information that must be protected according to relevant privacy laws and regulations.

📱 **Device Compatibility:** AFLogical OSE works best with Android devices running older versions. Some newer Android versions may have enhanced security features that limit logical extraction capabilities.

🔍 **Further Analysis:** The extracted CSV data can be analyzed using various forensic tools and techniques:
- **Excel/Google Sheets** - Basic data analysis and visualization
- **Autopsy** - Advanced forensic analysis platform
- **Timeline Analysis** - Chronological event reconstruction
- **Data Correlation** - Cross-referencing multiple data sources

💡 **Best Practices:**
- Always create forensic images before extraction
- Document all procedures and findings thoroughly
- Maintain chain of custody for evidence
- Use write-blocking techniques when possible

---

**🔗 Related Tools:**
- [Autopsy](https://www.autopsy.com/) - Digital forensics platform
- [Volatility](https://www.volatilityfoundation.org/) - Memory forensics framework
- [SIFT Workstation](https://digital-forensics.sans.org/community/downloads) - Forensic analysis toolkit

---

*📅 Last Updated: October 2025*
*👨‍💻 Author: Digital Forensics Lab*
