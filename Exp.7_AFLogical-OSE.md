
#  **Ex.No.7: Use AFLogical OSE to Extract Data from an Android Device**

##  **Description**
**AFLogical OSE (Open Source Edition)** is a specialized forensic tool designed for logical extraction of data from Android devices.  
This technique retrieves key user data—like contacts, call logs, and SMS messages—by leveraging the Android OS API, and does so typically without requiring root access.  
It is a fundamental component of the **Open Source Android Forensics toolkit**, essential for investigations and academic studies.

---

##  **STEP 1 — Initial Setup & File Extraction**

###  **Required Files (Pre-requisites)**
- **Android Platform Tools (ADB):** For device communication.  
- **AFLogical OSE ZIP (Source/APK):** The core forensic tool.  
- **Google USB Driver (for Windows):** To ensure PC-device connectivity.

###  **Instructions**
1. Create the primary lab folder:
   ```bash
   C:\DF
   ```
2. Extract all downloaded ZIP archives into this folder:
   ```bash
   C:\DF\platform-tools\
   C:\DF\aflogical-ose\
   C:\DF\usb-driver\
   ```
3. **Note on APK:**  
   If the AFLogical OSE ZIP doesn't include the `AFLogical-OSE.apk`, use a digital forensics OS like **Santoku Linux** to extract or build the APK from the source code.

---

##  **STEP 2 — Configure System Environment (PATH)**

###  **Purpose**
To enable the execution of `adb` commands directly from any Command Prompt or PowerShell window without specifying the full directory path.

###  **Steps**
1. Navigate to:  
   **Control Panel → System → Advanced system settings → Environment Variables**
2. Under *User Variables*, select **Path** and click **Edit**.
3. Click **New** and add the path:
   ```bash
   C:\DF\platform-tools
   ```
   <img width="610" height="673" alt="image" src="https://github.com/user-attachments/assets/bf3d4690-98b2-4afc-9dcc-1b88deef2e71" />

4. Click **OK** to save.

###  **Verification**
Open a Command Prompt and run:
```bash
adb version
```
<img width="1285" height="347" alt="image" src="https://github.com/user-attachments/assets/c16b02ed-1e48-4946-a562-043abb3e9e25" />

**Expected Output:**  
Displays the ADB version number (e.g., *Android Debug Bridge version 1.0.41*).

---

##  **STEP 3 — Install Google USB Driver (Windows Specific)**

###  **Purpose**
This driver allows Windows to identify and communicate with the connected Android device via ADB.

###  **Steps**
1. Connect the Android phone via USB.
2. Open **Device Manager** and locate the phone.
3. Right-click → **Update Driver** → **Browse my computer for drivers**.
4. Specify:
   ```bash
   C:\DF\usb-driver
   ```
5. Click **Next** to install.

###  **Verification**
Run:
```bash
adb devices
```
<img width="858" height="157" alt="image" src="https://github.com/user-attachments/assets/f84a2449-99e1-4a7f-8854-58f2964be372" />


**Expected Output:**  
Device listed without 'offline' or 'no permissions' status.

---

##  **STEP 4 — Prepare the Android Device (Developer Options)**

###  **Steps**
1. On the device:  
   **Settings → About phone → Tap "Build number" 7 times**
2. Go back to **Settings → Developer options**.
3. Enable:
   -  USB Debugging  
   -  Install via USB (if available)

---

##  **STEP 5 — Establish and Verify ADB Connection**

###  **Purpose**
To confirm a stable, authorized communication channel between the PC and Android device.

###  **Steps**
1. Ensure the phone is connected.
2. Run:
   ```bash
   adb devices
   ```
   

3. Tap **Allow** on the phone when prompted.

###  **Expected Output**

<img width="858" height="157" alt="image" src="https://github.com/user-attachments/assets/3bebf98b-8dab-4d04-ba44-1dc70d7d2d62" />

**Troubleshooting:**  
If *unauthorized*, replug cable and tap **Allow** again.

---

##  **STEP 6 — Deploy AFLogical OSE to the Device**

###  **Purpose**
Transfer and install the forensic APK onto the Android device.

###  **Steps**
1. Ensure APK is located at:
   ```bash
   C:\DF\aflogical-ose\AFLogical-OSE.apk
   ```
2. Install it:
   ```bash
   adb install --bypass-low-target-sdk-block "C:\Users\Manya\Downloads\DF\ForensicLab\AFLogical-OSE_1.5.2.apk"
   ```
   <img width="1464" height="183" alt="image" src="https://github.com/user-attachments/assets/b02f289c-3de4-42f5-90c1-518131a6e4f7" />



---

##  **STEP 7 — Execute Logical Data Extraction**

###  **Purpose**
Initiate data retrieval using AFLogical.

###  **Steps**
1. Open **AFLogical** on the device.  
2. Grant permissions (Contacts, SMS, Call Logs, Storage).  
3. Select:
   -  Contacts  
   -  SMS  
   -  Call Logs  
   -  MMS  
   -  Calendar  
4. Tap **Start Extraction**.  
5. Wait until extraction completes.

###  **Default Save Location**
```bash
/sdcard/aflogical/
```
or
```bash
/storage/emulated/0/aflogical/
```

---

##  **STEP 8 — Collect Extracted Data (Pull to PC)**

###  **Purpose**
Transfer extracted files from the device to the PC.

###  **Command**
```bash
adb pull /sdcard/aflogical C:\Users\Manya\Downloads
```
<img width="1358" height="173" alt="image" src="https://github.com/user-attachments/assets/545baf69-e750-410a-b07a-657d60b91e97" />

###  **Verification**
Files saved to:
```bash
C:\Users\Manya\Downloads
```
<img width="1254" height="361" alt="image" src="https://github.com/user-attachments/assets/22f021cb-f711-4268-88cb-eba0ed6c5684" />


---
---

##  **Result**

The experiment successfully demonstrated the logical extraction of user data from an Android device using **AFLogical OSE**.  
After configuring **ADB**, installing **AFLogical-OSE.apk**, and enabling **USB Debugging**, the tool extracted key artifacts such as **Contacts**, **SMS**, **Call Logs**, and **Calendar entries**.  

The extracted data was stored in:
```bash
/sdcard/aflogical/
```
## **Reference Links**
- **Android Platform Tools (ADB):** [https://developer.android.com/tools/releases/platform-tools](https://developer.android.com/tools/releases/platform-tools)  
- **Santoku Linux (Source for AFLogical OSE):** [https://sourceforge.net/projects/santoku/](https://sourceforge.net/projects/santoku/)  
- **Google USB Driver (Windows):** [https://developer.android.com/studio/run/win-usb](https://developer.android.com/studio/run/win-usb)

---

