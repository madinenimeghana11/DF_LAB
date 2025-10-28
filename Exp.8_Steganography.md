
# Ex.No.8 — Use StegExpose to Detect Hidden Data in Images

![StegExpose](https://img.shields.io/badge/Tool-StegExpose-green)
![Platform](https://img.shields.io/badge/Platform-Java-orange)
![Type](https://img.shields.io/badge/Analysis-Steganography-blue)

**📚 Course / Lab:** Digital Forensics Lab  
**🔢 Experiment No.:** 8  
**📝 Title:** Use StegExpose to Detect Hidden Data in Images

---

## 📑 Table of Contents

- [Ex.No.8 — Use StegExpose to Detect Hidden Data in Images](#exno8--use-stegexpose-to-detect-hidden-data-in-images)
  - [📑 Table of Contents](#-table-of-contents)
  - [📝 Description](#-description)
  - [🛠️ Prerequisites](#️-prerequisites)
  - [📋 Step-by-Step Process](#-step-by-step-process)
    - [Step 1: Download and Set Up StegExpose](#step-1-download-and-set-up-stegexpose)
    - [Step 2: Select Images for Analysis](#step-2-select-images-for-analysis)
    - [Step 3: Open Command Line or Terminal](#step-3-open-command-line-or-terminal)
    - [Step 4: Run StegExpose on an Image](#step-4-run-stegexpose-on-an-image)
    - [Step 5: Analyze the Output](#step-5-analyze-the-output)
    - [Step 6: Batch Analysis (Multiple Images)](#step-6-batch-analysis-multiple-images)
    - [Step 7: Advanced Options (Optional)](#step-7-advanced-options-optional)
    - [Step 8: Review the Results](#step-8-review-the-results)
  - [✅ Result](#-result)
  - [📝 Notes](#-notes)

---

## 📝 Description
**StegExpose** is a specialized tool used for **steganography analysis**. It works by evaluating the **statistical properties** of an image to estimate the probability of hidden data being embedded within it. This process helps forensic investigators detect steganography techniques like Least Significant Bit (LSB) embedding.

---

## 🛠️ Prerequisites

- **☕ Java Runtime Environment (JRE):** StegExpose is a Java-based application and requires JRE to run.
- **🔧 StegExpose Tool:** Download the latest `.jar` file from the official StegExpose GitHub repository.

---

## 📋 Step-by-Step Process

### Step 1: Download and Set Up StegExpose

**🎯 Purpose:** Set up the StegExpose environment for steganography detection.

**📋 Instructions:**
1. **📥 Download the tool:** Obtain the `StegExpose.jar` file from the GitHub repository.
2. **☕ Install Java:** Ensure JRE is installed on your machine.
3. **🗂️ Prepare environment:** Place the `StegExpose.jar` file in a dedicated working folder.

<details>
<summary>📂 View Setup Environment</summary>
<br>
<p align="center">
  <img width="600" alt="StegExpose setup environment" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/918625ec1e528d3a2721668acf6474e8c581c12a/images/8.1.png" />
</p>
</details>

---

### Step 2: Select Images for Analysis

**🎯 Purpose:** Prepare suspect images for steganographic analysis.

**📋 Instructions:**
- �️ Collect the images you suspect might contain hidden data.
- 📷 StegExpose supports common image formats such as **.png**, **.jpg**, and **.bmp**.

<details>
<summary>🖼️ View Image Selection</summary>
<br>
<p align="center">
  <img width="600" alt="Image files for analysis" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/918625ec1e528d3a2721668acf6474e8c581c12a/images/8.6.png" />
</p>
</details>

---

### Step 3: Open Command Line or Terminal

**🎯 Purpose:** Access the command line interface for running StegExpose.

**📋 Instructions:**
- 💻 Navigate to the folder where the `StegExpose.jar` file is located using your Command Prompt (Windows) or Terminal (Linux/macOS).

<details>
<summary>🖥️ View Command Line Navigation</summary>
<br>
<p align="center">
  <img width="700" alt="Command prompt navigation" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/918625ec1e528d3a2721668acf6474e8c581c12a/images/8.8.png" />
</p>
</details>

---

### Step 4: Run StegExpose on an Image

**🎯 Purpose:** Execute steganographic analysis on a single image file.

**💻 Command Structure:**
```bash
java -jar StegExpose.jar <image_file_path>
```

**📄 Example:**
```bash
java -jar StegExpose.jar test_image.png
```

---

### Step 5: Analyze the Output

**🎯 Purpose:** Interpret the steganographic analysis results.

📊 StegExpose calculates a **"suspect" score** ranging from 0 to 1. **The higher the score, the more likely steganography is present.**

**🎯 Threshold Values:**

| Score Range | Interpretation (Suggested Thresholds) |
| :---: | :--- |
| **✅ Less than 0.2** | Image is considered **clean** (no hidden data detected). |
| **⚠️ 0.2 - 0.3** | **Possibly** some hidden data is present. |
| **🚨 Above 0.3** | **Likely** that steganography is present. |

**📄 Example Output Analysis:**
```bash
java -jar StegExpose.jar suspect_image.png
```
```makefile
Analyzing suspect_image.png...
Result: 0.4
Steganography likely present
```

<details>
<summary>📊 View Analysis Results - Part 1</summary>
<br>
<p align="center">
  <img width="700" alt="StegExpose analysis output" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/918625ec1e528d3a2721668acf6474e8c581c12a/images/8.10.png" />
</p>
</details>

<details>
<summary>📊 View Analysis Results - Part 2</summary>
<br>
<p align="center">
  <img width="700" alt="StegExpose detailed results" src="https://github.com/baddiputi/Digital-Forensic-Lab-Exercises/blob/918625ec1e528d3a2721668acf6474e8c581c12a/images/8.11.png" />
</p>
</details>

---

### Step 6: Batch Analysis (Multiple Images)

**🎯 Purpose:** Analyze multiple images simultaneously for efficiency.

**📁 To check multiple images at once, specify the folder path containing the images:**

**💻 Command Structure:**
```bash
java -jar StegExpose.jar <folder_path>
```

**📄 Example:**
```bash
java -jar StegExpose.jar Images_to_Analyze
```

---

### Step 7: Advanced Options (Optional)

**🎯 Purpose:** Access additional StegExpose parameters and settings.

**❓ To view additional parameters, such as options for adjusting detection sensitivity or output verbosity, use the `--help` flag:**

**💻 Command:**
```bash
java -jar StegExpose.jar --help
```

---

### Step 8: Review the Results

**🎯 Purpose:** Evaluate analysis results and determine next steps.

**📋 Instructions:**
- 📊 Review the scores generated for each image
- 🎯 Use the threshold values to determine which images require further forensic investigation
- 🔍 Flag images with high suspect scores for detailed steganographic extraction

---

## ✅ Result

The hidden data within the image was successfully detected using StegExpose. The analysis revealed that images with a suspect score above the threshold likely contain embedded steganographic content, confirming the tool's effectiveness in steganography detection.

🎯 **Key Achievements:**
- ✅ Successfully configured and executed StegExpose for steganographic analysis
- ✅ Analyzed both single images and batch processing of multiple images
- ✅ Interpreted suspect scores using established threshold values
- ✅ Identified images with high probability of containing hidden data
- ✅ Demonstrated effective steganography detection methodology

**📊 Analysis Summary:**
- 🔍 **Detection Method:** Statistical property analysis
- 📈 **Scoring System:** 0-1 scale with threshold-based interpretation
- 🎯 **Effectiveness:** Successfully identified steganographic content
- 📋 **Documentation:** Complete analysis workflow established

---

## 📝 Notes

⚠️ **Detection vs. Extraction**: StegExpose is a detection tool. It identifies the likelihood of hidden data presence but does not extract the actual hidden content.

📊 **Statistical Analysis**: The tool analyzes statistical anomalies in image properties that typically occur when data is embedded using steganographic techniques.

🔍 **Further Investigation**: Images flagged with high suspect scores should be analyzed with extraction tools like Steghide or StegSolve to recover hidden data.

🎯 **Threshold Guidance**: The suggested thresholds (0.2, 0.3) are guidelines. Actual thresholds may vary based on specific investigation requirements and image types.

---

**🔗 Related Tools:**
- [Steghide](https://github.com/StefanoDeVuono/steghide) - For extracting hidden data
- [StegSolve](http://www.caesum.com/handbook/Stegsolve.jar) - Advanced steganography analysis
- [Binwalk](https://github.com/ReFirmLabs/binwalk) - Firmware analysis and extraction

---

*📅 Last Updated: October 2025*
*👨‍💻 Author: Digital Forensics Lab*
