
# Ex.No.8 — Detect Hidden Data in Images Using zsteg (Linux)

## Aim
To detect and extract hidden or steganographic data from image files using the **zsteg** tool in Linux.

## Introduction
Steganography is the process of hiding information within digital media such as images or audio files. Cybercriminals may use this technique to conceal malicious payloads or secret messages. **zsteg** is a powerful open-source tool that detects and extracts hidden data from PNG and BMP files using Least Significant Bit (LSB) steganography and other common methods. This experiment demonstrates how to analyze and extract such hidden data using zsteg.

## Required Software (Download / Install Before Starting)
```bash
sudo apt update
sudo apt install ruby ruby-dev build-essential
sudo gem install zsteg
sudo apt install imagemagick  # optional for image visualization
```

## Procedure
1. Open the terminal on your Linux system.  
2. Place the suspect image file (e.g., `suspect.png`) in your working directory.  
3. Run zsteg to analyze the image for hidden data:  
   ```bash
   zsteg dog.png
   ```
   <p align="center">
       <img width="811" height="293" alt="image" src="https://github.com/user-attachments/assets/7b2cf64d-d74e-499c-8908-906bbd9c6cae" />
   </p>
<br>
<br>
<p align="center">
   <img width="820" height="303" alt="image" src="https://github.com/user-attachments/assets/6284c368-417c-4d8b-9e0f-84bb7b771dbe" />
</p>

4. To analyze all PNG files in a folder:  
   ```bash
   for f in *.png; do echo "=== $f ==="; zsteg "$f"; done
   ```
<p align="center">
  <img width="1694" height="922" alt="image" src="https://github.com/user-attachments/assets/8cc4d624-4e9c-4cb0-a527-7248fae190ce" />
</p>


5. When zsteg detects hidden data, extract it using the `-E` flag:  
   ```bash
   zsteg -E all suspect.png > extracted_data.bin
   ```
6. Check the extracted file type and content:  
   ```bash
   file extracted_data.bin
   strings extracted_data.bin | less
   hexdump -C extracted_data.bin | head
   ```
7. Record findings such as file name, detection method, and extracted data type.



## Result
Hidden information was successfully detected and extracted from the given image using **zsteg** on Linux.

## Notes
- **zsteg** works best on PNG and BMP images.  
- Always analyze copies of original evidence.  
- Use checksum tools like `sha256sum` to verify file integrity.  
- Try specific color channels if no data is found:  
  ```bash
  zsteg -E bgr,lsb,xy,1 suspect.png
  ```

