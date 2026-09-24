
# 🧪 EXPERIMENT 06 — Digital Evidence Analysis and File Recovery Using The Sleuth Kit (TSK)

---

## 🎯 Objective

To conduct a forensic analysis of a disk image using **The Sleuth Kit (TSK)** command-line utilities, identify the file-system structure, extract file-system metadata, locate deleted files, recover deleted digital evidence, analyze file metadata, and generate a chronological file activity body file for forensic investigation.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows, Linux, or macOS
* **Forensics Toolkit:** The Sleuth Kit (TSK)
* **Optional Tool:** OSFMount
* **Evidence File:** `4Dell Latitude CPi.E01`
* **TSK Version:** 4.14.0
* **Command-Line Interface:** Windows Command Prompt

The following TSK utilities were used:

* `mmls`
* `fsstat`
* `fls`
* `istat`
* `icat`
* `mactime`

---

## 📋 Experiment Scenario

The Sleuth Kit (TSK) is an open-source collection of command-line forensic utilities used to examine disk images and file systems.

TSK allows investigators to examine digital evidence at the disk and file-system level without relying on the normal operating-system file-access mechanisms.

The toolkit can be used to:

* Analyze partition structures
* Identify file-system offsets
* Extract file-system information
* List files and directories
* Identify deleted files
* Examine file metadata
* Recover file contents
* Extract MAC timestamps
* Construct chronological file activity timelines

The experiment used the forensic disk image:

```text
4Dell Latitude CPi.E01
```

The analysis identified an NTFS partition beginning at sector **63** and used this offset for subsequent file-system operations.

---

# ⚙️ Procedure

## Step 1 — Verify The Sleuth Kit Installation

The Windows Command Prompt was opened with administrative privileges.

The directory containing the TSK executable files was accessed.

The working directory used was:

```text
C:\Users\SADHAN\Downloads\sleuthkit-4.14.0-win32(1)\sleuthkit-4.14.0-win32\bin
```

The `fls` version command was executed to verify that The Sleuth Kit was installed correctly.

### Command

```text
cd /d "C:\Users\SADHAN\Downloads\sleuthkit-4.14.0-win32(1)\sleuthkit-4.14.0-win32\bin"
fls -V
```

The installed TSK version was displayed successfully.

📸 **Figure 1:** Verifying The Sleuth Kit installation and version.

---

# 🔍 Step 2 — Partition Analysis Using `mmls`

The `mmls` utility was used to examine the partition layout of the forensic disk image.

The purpose of this step was to identify the starting sector of the relevant file-system partition.

### Syntax

```text
mmls [image_file]
```

### Command Executed

```text
mmls.exe "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01"
```

The output showed that the primary **NTFS file system started at sector 63**.

This sector value was used as the file-system offset for the subsequent TSK commands.

📸 **Figure 2:** `mmls` output showing the NTFS partition beginning at sector 63.

---

# 📊 Step 3 — File-System Analysis Using `fsstat`

The `fsstat` utility was used to extract detailed information about the NTFS file system.

The `-o 63` option was used to specify the partition starting offset identified using `mmls`.

The output was redirected to a text file for documentation.

### Syntax

```text
fsstat -o [offset] [image_file] > [output.txt]
```

### Command Executed

```text
fsstat.exe -o 63 "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01" > filesystem_info.txt
```

The generated file was:

```text
filesystem_info.txt
```

The output contained technical information about the file system and its underlying structures.

📸 **Figure 3:** Generating and viewing `filesystem_info.txt`.

---

# 🔎 Step 4 — File and Directory Analysis Using `fls`

The `fls` utility was used to list files and directories present within the forensic image.

The recursive `-r` option was used to examine the directory structure throughout the partition.

The partition offset was specified using `-o 63`.

### Syntax

```text
fls -o [offset] -r [image_file] > [output.txt]
```

### Command Executed

```text
fls -o 63 -r "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01" > file_list.txt
```

The generated file was:

```text
file_list.txt
```

The resulting file list was examined for deleted entries.

In TSK output, deleted entries can be identified using an asterisk (`*`).

The analysis identified the deleted file:

```text
wizdata.dat
```

with inode:

```text
10091
```

📸 **Figure 4:** Searching `file_list.txt` and identifying the deleted `wizdata.dat` file at inode 10091.

---

# 🧬 Step 5 — File Metadata Analysis Using `istat`

After identifying the inode number, the `istat` utility was used to examine the detailed metadata associated with the deleted file.

The identified inode was:

```text
10091
```

### Syntax

```text
istat -o [offset] [image_file] [inode_number] > [output.txt]
```

### Command Executed

```text
istat -o 63 "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01" 10091 > metadata_info.txt
```

The generated file was:

```text
metadata_info.txt
```

The metadata was examined to identify information such as:

* File type
* File size
* Inode information
* File-system metadata
* Modified timestamp
* Accessed timestamp
* Changed timestamp
* Data block information

The three important file-system timestamps are commonly referred to as **MAC times**:

* **Modified (M)** — when file content was modified
* **Accessed (A)** — when the file was accessed
* **Changed (C)** — when relevant file metadata changed

📸 **Figure 5:** `istat` output showing metadata for inode 10091.

---

# 💾 Step 6 — Deleted File Recovery Using `icat`

The `icat` utility was used to recover the contents associated with the deleted file.

The inode identified during the previous analysis was:

```text
10091
```

### Syntax

```text
icat -o [offset] [image_file] [inode_number] > [output_file]
```

### Command Executed

```text
icat -o 63 "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01" 10091 > recovered_wizdata.dat
```

The recovered file was saved as:

```text
recovered_wizdata.dat
```

This demonstrated how TSK can extract file contents directly from the forensic disk image using the identified inode.

📸 **Figure 6:** Successful recovery of `wizdata.dat` using the `icat` command.

---

# 🕒 Step 7 — Generate the Forensic Body File

The `fls` command was used with the `-m` option to generate a machine-readable **body file** containing file-system metadata and MAC timestamps.

The recursive option was also used to process the complete partition.

### Syntax

```text
fls -o [offset] -m / -r [image_file] > [body.txt]
```

### Command Executed

```text
fls -o 63 -m / -r "C:\Users\SADHAN\Downloads\4Dell Latitude CPi.E01" > body.txt
```

The generated file was:

```text
body.txt
```

The body file contains machine-readable information that can be used to reconstruct the chronological activity of files within the forensic image.

📸 **Figure 7:** Generating the raw forensic `body.txt` file.

---

# 🕐 Timeline Analysis

The TSK `mactime` utility can normally be used to convert the body file into a human-readable chronological timeline.

### Standard Syntax

```text
mactime -b body.txt > timeline.txt
```

However, in this Windows forensic workstation, the `mactime` utility required a Perl interpreter to execute.

A native Perl interpreter such as **Strawberry Perl** or **ActivePerl** was not configured on the workstation during this experiment.

Therefore, the following step was not executed:

```text
mactime -b body.txt > timeline.txt
```

Instead, the generated:

```text
body.txt
```

file was examined directly.

The body file contained the machine-readable MAC timestamp information required for chronological file-activity analysis.

📸 **Figure 8:** Examining the generated body file containing chronological MAC timestamp information.

---

# 🔎 Forensic Findings & Analysis

## 1. Partition Analysis

The `mmls` utility successfully analyzed the partition structure of the forensic disk image.

The primary NTFS partition was identified as beginning at:

```text
Sector: 63
```

This value was used as the offset for subsequent TSK commands.

---

## 2. File-System Analysis

The `fsstat` utility successfully extracted technical information about the NTFS file system.

The output was saved as:

```text
filesystem_info.txt
```

This provided information about the structure and characteristics of the file system.

---

## 3. Deleted File Identification

The recursive `fls` analysis produced a complete file and directory listing.

Deleted entries were identified by examining the TSK output for the deleted-file indicator.

The following deleted file was identified:

```text
wizdata.dat
```

Its inode number was:

```text
10091
```

---

## 4. File Metadata Analysis

The `istat` utility was used to examine inode `10091`.

The metadata provided information about the identified file, including its MAC timestamps and file-system information.

This information can be useful for reconstructing file activity during a forensic investigation.

---

## 5. Deleted File Recovery

The `icat` utility successfully recovered the contents associated with inode `10091`.

The recovered evidence was saved as:

```text
recovered_wizdata.dat
```

This demonstrated the ability of TSK to recover file content directly from a forensic disk image.

---

## 6. Timeline Data Generation

The `fls` command successfully generated a machine-readable body file:

```text
body.txt
```

The body file contained MAC timestamp information for file-system entries.

Although `mactime` was not executed because the required Perl environment was unavailable, the body file itself provided the raw chronological information required for subsequent timeline reconstruction.

---

# 🧠 Findings

* The Sleuth Kit was successfully installed and verified.
* The `mmls` utility identified the NTFS partition starting at sector **63**.
* The `fsstat` utility successfully extracted NTFS file-system information.
* The `fls` utility recursively listed files and directories within the forensic image.
* The deleted file `wizdata.dat` was identified at inode **10091**.
* The `istat` utility provided detailed metadata for inode `10091`.
* The `icat` utility successfully recovered the deleted file contents.
* A machine-readable forensic body file was successfully generated.
* The body file contained MAC timestamp information useful for chronological event reconstruction.
* The `mactime` step was not performed because a Perl interpreter was not configured on the Windows workstation.

---

# 🛡️ Forensic Significance

The experiment demonstrates how **The Sleuth Kit** can be used to investigate a forensic disk image at the partition and file-system level.

The combination of:

```text
mmls → fsstat → fls → istat → icat → body file
```

provides a practical forensic workflow for:

* Identifying partitions
* Understanding file systems
* Locating deleted files
* Examining metadata
* Recovering file contents
* Extracting historical file activity information

The analysis was performed against the forensic disk image rather than modifying the original evidence source.

---

# 📊 Result

✅ **Experiment Successfully Completed**

The `4Dell Latitude CPi.E01` forensic disk image was successfully analyzed using **The Sleuth Kit** command-line utilities.

The `mmls` command identified the NTFS partition at sector **63**. The file system was analyzed using `fsstat`, and the recursive `fls` command identified the deleted file `wizdata.dat` at inode **10091**.

The file metadata was examined using `istat`, and the deleted file was successfully recovered using `icat`.

A machine-readable `body.txt` file containing MAC timestamp information was also generated to support chronological file-activity reconstruction.

---

# 📝 Conclusion

The experiment demonstrated the practical application of **The Sleuth Kit (TSK)** for digital evidence analysis and deleted-file recovery.

The forensic disk image was examined at the partition and file-system levels without relying on normal operating-system file-access mechanisms.

Using TSK utilities, the NTFS partition structure was identified, file-system information was extracted, a deleted file was located through its inode, metadata was examined, and the deleted file contents were successfully recovered.

The generation of the forensic body file further demonstrated how file-system timestamps can be collected for chronological event reconstruction.

Although the `mactime` conversion step was not performed because a Perl interpreter was unavailable on the Windows workstation, the required raw MAC timestamp information was successfully generated in `body.txt`.

Overall, the experiment provided practical experience in **disk-image analysis, file-system examination, deleted-file identification, metadata analysis, file recovery, and forensic timeline preparation using The Sleuth Kit**.
