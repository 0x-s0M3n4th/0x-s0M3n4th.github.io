---
title: "Practical Demo: Creating a Forensic Image with FTK Imager"
date: 2025-11-02T19:50:00+05:30  
draft: false                    
description: "A step-by-step walkthrough of acquiring a disk image using Exterro's FTK Imager, a critical tool for digital forensics and incident response."
tags:
  - "Forensics"
  - "FTK Imager"
  - "Disk Imaging"
  - "Incident Response"
toc: true
---
# What is ftk imager?
**FTK Imager** is a free, forensic tool used to create a bit-by-bit copy, or "image," of a storage device to preserve it as evidence without altering the original data. It is used by digital investigators to collect and analyze electronic evidence from various sources like hard drives, mobile devices, and removable media. A key feature is its ability to perform integrity checks using hashing algorithms to ensure the forensic image is an accurate and authentic copy, which is crucial for legal admissibility.


## Real-World Applications of FTK Imager:

FTK Imager finds extensive use in various domains within digital forensics:

### 1. Digital Crime Investigations:

- FTK Imager assists in collecting evidence for criminal cases, helping investigators build strong cases based on accurate and comprehensive forensic images.

### 2. Incident Response:

- During incident response activities, FTK Imager aids in analyzing compromised systems, identifying potential threats, and providing valuable insights into the nature of the incident.

### 3. E-Discovery:

- FTK Imager plays a crucial role in e-discovery, allowing for the extraction and analysis of electronic data for legal purposes. This enables organizations to comply with legal requirements and uncover relevant evidence.

### 4. Data Recovery:

- In cases involving data loss or deletion, FTK Imager helps retrieve lost or deleted files, providing investigators with critical information for their examinations.

---
# Practical Demo:
partition creation -> Transferring any file into that partition -> removing it -> creating an image of that partition -> opening it through ftk imager again and seeing if we can see the deleted data or not.

## Creating a separate partition for the practical:
1. Open `file manager` -> click on `This pc` -> You may have multiple partition / may not. 
2. Now click on the `windows` button, search for `disk management` , and open it:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_1_prac_1.png)
3. You should see your primary partition, right click on it
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_2_prac_1.png)
4. Then select the option `shrink volume` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_3_prac_1.png)
5. We only need 1 gb for the partition, to do so write `1024` into this column , and then click on `shrink`:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_4_prac_1.png)
6. There should be a new `unallocated` volume created:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_5_prac_1.png)
7. Again right click on that newly created volume and select the option `New simple volume` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_6_prac_1.png)
8. A wizard like this will pop up, click on `next` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_7_prac_1.png)
9. select the default stuffs, and give it a name accordingly, i have given the name `FTK`
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_8_prac_1.png)
10. Then click on finish 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_9_prac_1.png)
11. The new partition will appear.
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_10_prac_1.png)

## Installing ftk imager:
1. Search for ftk imager download, come to this following website and click on `free download` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_11_prac_1.png)
2. Install the application first on your own.

---
## Now let's start  the actual practical:
1. Select any image of your choice from your any folder, copy and paste that image into the newly created partition you just made for the practical. After pasting delete it immediately.
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_12_prac_1.png)

2. Now open `ftk imager application` -> Click on `file` and select the option `create disk image` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_13_prac_1.png)
3. Then select `logical dirve` -> then select the drive you want to make an image of , then another wizard will pop up after finishing the previous step, click on `add` option. Then select the option `E01` , then give a basic description as you need.
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_14_prac_1.png)
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_15_prac_1.png)
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_16_prac_1.png)
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_17_prac_1.png)
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_18_prac_1.png)
4. Then select a destination folder to store the img file:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_19_prac_1.png)
5. After that click on start:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_20_prac_1.png)
6. The image will be created:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_21_prac_1.png)
7. Go to the destination location, we can see two files are there:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_22_prac_1.png)
8. First one is a text doc, which will provide us basic info of the case
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_23_prac_1.png)
9. Second one is the actual image the `EO1` file .

---
_KEY FEATURES OF EO1 FILE:_


When you create the `.E01` file, you are embedding several critical pieces of data directly into the file itself.

1. **Case Metadata (The Label)**:

- At the start of the process, FTK Imager asks you for "Evidence Item Information."

- This includes Case Number, Examiner Name, Notes, Evidence Number, etc.

- All this information is written into the .E01 file's header. This is a core part of the Chain of Custody—it proves who collected the evidence, when, and why.

2. **Built-in Verification (The Tamper-Proof Seal)**:

- This is the most important feature.

- The .E01 format saves `MD5` and/or `SHA1` hashes for the entire evidence source.

- When you "verify" the image (or when another tool opens it), it re-calculates the hash of the data and compares it to the original hash stored in the file.

- If they match: You can state in court that your forensic copy is a perfect, unaltered duplicate of the original drive.

- If they don't match: The evidence is considered "tampered" or "corrupted."

3. **Compression (To Save Space)**:

- The raw data inside the `.E01` container is compressed.

- This is why your 500 GB drive might result in a 200 GB .E01 file. It intelligently skips empty space and compresses the rest.

4. **File Segmentation (Chunking)**:

- The E01 format automatically splits the image into smaller, manageable "chunks."

- You will see files like `image.E01, image.E02, image.E03`, etc.

- This was originally done because many file systems (like `FAT32`) couldn't handle single files larger than 4 GB. This standard just continued.

- The `.E01` file is the "main" file that holds the headers, metadata, and the first chunk of data.

---
## Image analysis:
1. Come to `ftk imager app` -> select `add evidence item` -> this time use the option `image file`
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_24_prac_1.png)
2. select the `image file` from the source location:
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_25_prac_1.png)
3. On finishing the step and `evidence tree` will appear on the left pane. Click through the tree until you find the option `Recycle Bin` 
![FTK_1](/images/UNI_PRACS/INT_250/int_250_ss_26_prac_1.png)
4. And we can see the image file we previously deleted.
