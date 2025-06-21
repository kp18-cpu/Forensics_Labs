# Digital Forensics Lab Portfolio: Unveiling Digital Truths

This repository showcases my in-depth practical experience and theoretical understanding in the field of digital forensics. Through a series of comprehensive labs, I've mastered various tools and techniques to acquire, analyze, and interpret digital evidence across different operating systems and storage media.

## Labs & Key Learnings:

My work spans foundational concepts to advanced memory and disk analysis, demonstrating proficiency in both open-source and commercial forensic tools.

### 1. Disk Imaging & Hashing (Lab: Imaging with DD and LiME)
* **Forensic Duplication:** Gained hands-on experience in creating bit-for-bit copies (forensic images) of physical drives using industry-standard tools like **FTK Imager** and command-line utilities like `dd`. 
* **Hashing for Integrity:** Learned to compute and verify cryptographic hashes (MD5 and SHA1) of both original drives and their forensic images to ensure data integrity and demonstrate that the image is an exact replica of the source. 
* **Network Imaging with Netcat:** Performed remote disk imaging over a network using `dd` piped to `netcat`, a crucial skill for acquiring evidence from live systems. 
* **Memory Acquisition (LiME):** Acquired volatile memory (RAM) from a live Linux system using the **LiME (Linux Memory Extractor)** tool, understanding its importance in capturing transient evidence. 

### 2. File System Analysis (Lab: Disk analysis Autopsy)
* **Partition Identification:** Identified disk partitions and their offsets using `fdisk -l`. 
* **File System Type Determination:** Determined file system types (e.g., Ext4, Ext2, FAT16) and identified superblock information (e.g., block size) using tools like `fsstat` and `dumpe2fs`. 
* **Mounting Forensic Images:** Safely mounted forensic images in a read-only manner using specific offset calculations for analysis. 
* **Deleted File Recovery:** Utilized Sleuthkit commands (`fls`, `ils`) to list and analyze deleted files and directories, including unallocated and reallocated inodes. 
* **Timeline Creation:** Generated comprehensive timelines of file activities (`flsMactime`, `ilsMactime`) to reconstruct events, highlighting the value of temporal analysis in investigations. 
* **Inode and Data Block Examination:** Used `istat` to view inode details and `icat` / `blkcat` to dump data from specific inodes and data blocks, understanding the relationship between them. 
* **File Carving (Foremost):** Employed `foremost` to recover deleted or fragmented files (e.g., JPEG, PDF) from raw disk images based on file headers and footers. 

### 3. Windows Registry Forensics (Lab: Windows Registry & Volatility Usage)
* **Registry Hive Analysis (AccessData Registry Viewer):** Explored key Windows Registry hives (SAM, SYSTEM, SOFTWARE, NTUSER.DAT) to extract crucial user and system configuration data. 
* **User Activity Tracing:** Identified logged-on users, password change times, and previously connected USB devices by analyzing specific Registry keys (e.g., `SAM>Domains>Account>Users`, `Enum>USBSTOR`). 
* **System Configuration Details:** Retrieved system-level information like Time Zone settings and active Control Sets. 
* **Web Activity Analysis:** Extracted visited URLs from `TypedURLs` within `NTUSER.DAT`. 
* **Automated Registry Analysis (RegRipper):** Used `RegRipper` with its various plugins to automate the extraction of specific artifacts from Registry hives, such as USB connection details, user-assisted applications, and system shutdown times. 

### 4. Memory Forensics (Lab: Volatility Usage)
* **Volatility Framework (Windows):** Utilized **Volatility 2.6.1** and **Volatility 3** to perform in-depth memory analysis of Windows `vmem` images. 
* **Process Analysis:** Compared `pslist` and `psscan` to identify running and potentially hidden (unlinked) processes, and used `pstree` to visualize process hierarchies. 
* **Network Connection Forensics:** Identified active and previous TCP/UDP connections using `connections` and `connscan`/`netscan`, and traced connections back to originating processes. 
* **Registry in Memory:** Extracted Registry hive paths and identified suspicious executables (`sdra64.exe`) from `Winlogon`'s `Userinit` key using `hivelist` and `printkey`. 
* **Hidden Code Detection (`malfind`):** Used `malfind` to detect injected or hidden code within process memory, a key step in identifying malware. 
* **Volatility (Linux):** Performed basic Linux memory analysis using `linux_pslist`, `linux_bash` (previous commands), `linux_netstat` (network statistics), `linux_banner` (OS version), and `linux_lsmod` (loaded modules) on `bin` memory dumps. 

### 5. Advanced Forensic Toolkit (FTK) Lab
* **Evidence Refinement & Processing:** Configured and understood default settings for evidence and index refinement (e.g., file slack, free space, hashing, bad extensions, deleted files). 
* **Evidence Types:** Identified various types of evidence that can be added to an FTK case (acquired images, physical drives, individual files, etc.). 
* **Partition and File System Identification:** Used FTK to automatically identify partitions (e.g., NTFS, Ext2) and their file systems within a disk image. 
* **Recycle Bin Analysis:** Located and analyzed deleted files from the Windows Recycle Bin, identifying the owning user by their SID. 
* **File Category & Path Analysis:** Categorized files (e.g., Documents, Graphics) and traced their full file paths. 
* **Document Metadata Extraction:** Extracted author, last modified date, and last modifier from document properties. 
* **Foreign Language Detection:** Identified documents written in foreign languages (e.g., Arabic, Japanese). 
* **Internet History & Artifacts:** Found Google search terms (e.g., "atm card stealing") and other web-related artifacts from temporary internet files (`index.dat`). 
* **Video & Image Analysis:** Viewed multimedia files and extracted details from images. 
* **Registry Analysis (FTK):** Explored Registry entries for hidden keyloggers and driver information. 
* **Bad Extensions & Carved Files:** Categorized files with mismatched extensions and successfully performed data carving to recover fragmented images and other files. 
* **Credit Card Number Extraction:** Identified credit card numbers (e.g., Visa) from unallocated space. 
* **Indexed vs. Live Search:** Understood the advantages of indexed search for speed versus live search for thoroughness. 
* **Email Analysis:** Identified email conversations and extracted pertinent information from emails, including suspicious offers and attachments. 
* **File Shredding Detection:** Identified instances of file shredding, indicating attempts to securely erase data. 
* **Tagged Files:** Marked suspicious files for further review and reporting. 

### 6. Steganography & Anti-Forensics (Lab: Steganography)
* **Steganography Detection:** Identified hidden files within images (e.g., `.jpg` carrier files) and extracted them using specialized tools like Invisible Secrets. 
* **Password Recovery for Steganography:** Recovered passwords used to encrypt and hide steganographic data. 
* **Anti-Forensics Techniques (Theoretical & Practical):**
    * **Evidence Destruction:** Explored techniques to destroy digital evidence, including overwriting drives (Eraser), deleting event logs, and disabling last access time updates. 
    * **Obfuscation:** Understood methods to obfuscate digital footprints, such as using steganography and timestomping. 
    * **Automated Anti-Forensics:** Designed and analyzed a simple batch script malware to clear Windows logs and monitor device insertions, highlighting how attackers automate anti-forensic measures. 
    * **Advanced Malware Techniques:** Understood concepts like file-less malware (WMI), Alternate Data Streams (ADS), and Reflective DLL Injection for stealthy operations. 
    * **USB Device History Erasure:** Learned to delete records of previously connected USB devices using tools like USBDeview. 
    * **Shadow Copy Disablement:** Disabled the Volume Shadow Copy Service (VSS) to prevent creation of system snapshots. 
    * **User Hash Deletion:** Explored methods to delete user-specific hashes from the Registry to increase anonymity. 
    * **Timestomping:** Modified file timestamps (creation, access, modification, metadata change) using tools like `nTimetools` to mislead investigators. 
* **Bulk Extractor Usage:** Used `bulk_extractor` for rapid, thorough analysis of large datasets, identifying emails, domains, and other features, even from unallocated space. 

### 7. Digital Forensics Reporting (Final Project)
* **Case Scenario Analysis:** Applied forensic investigation skills to a realistic case scenario involving financial fraud and data theft. 
* **Evidence Correlation:** Correlated evidence from various sources (emails, documents, internet history, system artifacts) to build a compelling narrative. 
* **Report Generation:** Produced detailed forensic reports, including statements, supporting evidence, and conclusions, demonstrating effective communication of findings. 

## Demonstrated Expertise:

* **Tool Proficiency:** Highly proficient in a wide array of digital forensic tools, including FTK Imager, AccessData Forensic Toolkit (FTK), Volatility Framework (v2 & v3), Sleuthkit, Autopsy, LiME, `dd`, `netcat`, `strings`, `foremost`, `RegRipper`, `John the Ripper`, `Crunch`, `Mimikatz`, `Ophcrack`, and various anti-forensics utilities.
* **Operating System Agnostic Analysis:** Capable of performing forensic analysis on both Windows and Linux memory and disk images.
* **Comprehensive Evidence Collection:** Skilled in identifying and acquiring various types of digital evidence, from volatile memory to persistent storage artifacts.
* **Data Recovery & Reconstruction:** Proficient in recovering deleted files, carving data, and reconstructing user activities and system events.
* **Vulnerability & Attack Understanding:** Possesses a deep understanding of common digital attacks (e.g., steganography, file shredding, password cracking, malware anti-forensics) and the forensic techniques used to counter them.
* **Analytical & Critical Thinking:** Demonstrated ability to analyze complex digital data, identify suspicious patterns, and draw reasoned conclusions.
* **Reporting & Communication:** Capable of documenting forensic processes and presenting findings clearly and concisely in professional reports.

This repository serves as a testament to my dedication to digital forensics, showcasing a robust skill set ready to tackle real-world investigative challenges.
