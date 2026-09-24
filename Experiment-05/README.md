
# 🧪 EXPERIMENT 05 — Digital Forensics Investigation Using Autopsy: Case Creation and Evidence Import

---

## 🎯 Objective

To use the **Autopsy Digital Forensics Platform** to create a new forensic case, import a disk image evidence file, configure ingest modules, perform basic forensic analysis, examine digital artifacts, and generate a forensic investigation report.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows, Linux, or macOS
* **Forensics Tool:** Autopsy Digital Forensics Platform
* **Evidence Files:**

  * `4Dell Latitude CPi.E01`
  * `4Dell Latitude CPi.E02`
* **Evidence Type:** EnCase Expert Witness Format (`.E01`)

---

## 📋 Experiment Scenario

Autopsy is an open-source digital forensics platform that provides a graphical interface for **The Sleuth Kit** and other forensic analysis components.

In a digital forensic investigation, forensic evidence is normally acquired as a disk image rather than by directly modifying the original storage device.

Autopsy allows investigators to create a dedicated **Case**, add forensic data sources, process evidence using **Ingest Modules**, identify digital artifacts, examine deleted files and file-system information, and generate investigation reports.

The experiment focused on:

* Creating a forensic case
* Recording case and examiner information
* Importing an `.E01` disk image
* Configuring ingest modules
* Processing forensic evidence
* Examining file-system artifacts
* Investigating deleted files
* Viewing file metadata
* Reviewing extracted artifacts
* Generating a forensic report

---

# ⚙️ Procedure

## Step 1 — Installation & Preparation

Autopsy was installed and launched on the forensic analysis workstation.

The required evidence files were downloaded from the provided forensic repository and stored in a dedicated evidence directory.

The evidence files used for the experiment were:

```text
4Dell Latitude CPi.E01
4Dell Latitude CPi.E02
```

The `.E01` and `.E02` files were kept in the same directory because they represent segments of the same forensic disk image.

📸 **Figure 1:** Autopsy startup screen and application interface.

---

## Step 2 — Create a New Forensic Case

Autopsy was launched and the **New Case** option was selected.

The following case information was entered:

**Case Name:**

```text
Sadhan_99240041226
```

**Case Number:**

```text
99240041226
```

**Examiner Name:**

```text
Sadhan
```

A dedicated directory was selected as the location for storing the case data.

The case was then created successfully.

📸 **Figure 2:** Creating a new forensic case and specifying the case directory.

📸 **Figure 3:** Entering case number and examiner information.

---

## Step 3 — Add the Disk Image Evidence

After creating the case, the **Add Data Source** option was selected.

The data-source type was configured as:

**Disk Image or VM File**

The following evidence file was selected:

```text
4Dell Latitude CPi.E01
```

The `.E02` segment was kept in the same directory so that Autopsy could access the complete segmented evidence image.

The evidence source was added to the case for forensic processing.

📸 **Figure 4:** Selecting the `.E01` disk image as the forensic data source.

---

## Step 4 — Configure Ingest Modules

Autopsy provides **Ingest Modules** that automatically process the imported evidence and identify forensic artifacts.

The required modules were selected according to the investigation requirements.

Examples of modules that may be enabled include:

* Recent Activity
* Hash Lookup
* File Type Identification
* Keyword Search
* Embedded File Extraction
* Picture Analyzer
* Interesting Files Identifier
* Extension Mismatch Detector
* EXIF Parser

The selected modules were configured and the ingest process was started.

📸 **Figure 5:** Selecting and configuring Autopsy Ingest Modules.

---

## Step 5 — Monitor Ingest Processing

After starting the ingest process, Autopsy processed the disk image in the background.

The **Ingest Inbox/Progress** area was monitored to observe the processing status.

Autopsy analyzed the evidence and automatically categorized the discovered information into different forensic artifact categories.

Examples include:

* File System
* Deleted Files
* Web Artifacts
* Images
* Audio
* Video
* Documents
* Email
* User Accounts
* Recent Activity

📸 **Figure 6:** Autopsy ingest progress and processed forensic evidence.

---

# 🔎 Forensic Analysis

## 1. File System Analysis

The **File System** section was examined to identify the files and directories contained within the disk image.

The investigator can navigate through directories and inspect individual files.

Information such as:

* File name
* File path
* File size
* File type
* Created time
* Modified time
* Accessed time

can be examined.

📸 **Figure 7:** Examining the file system and directory structure.

---

## 2. Deleted File Analysis

The **Deleted Files** section was examined to identify files that had been marked as deleted within the file system.

Deleted-file analysis can help investigators identify potentially relevant artifacts that may still be recoverable or whose metadata remains available.

📸 **Figure 8:** Viewing deleted files identified by Autopsy.

---

## 3. File Type Analysis

The **File Types** section was examined to categorize files according to their types.

Examples include:

* Images
* Audio
* Video
* Documents
* Archives
* Executables

An individual file can be selected to examine its available metadata and content.

📸 **Figure 9:** File Type categorization and forensic artifact analysis.

---

## 4. File Metadata Examination

An individual forensic artifact was selected for detailed examination.

Depending on the file type, Autopsy can display information such as:

* File name
* File path
* File size
* MIME type
* File-system timestamps
* Hash values
* File metadata
* Extracted content

Different viewing options may also be available depending on the artifact.

📸 **Figure 10:** Detailed file examination and metadata view.

---

## 5. Hash Analysis

Hash information can be used to identify and compare digital evidence.

Autopsy can calculate hashes for files and, when configured, compare them against known hash databases.

Hash analysis can assist investigators in identifying known files and documenting evidence integrity.

📸 **Figure 11:** File hash information displayed in Autopsy.

---

# 📊 Reporting

## Step 1 — Generate Report

After completing the forensic examination, the **Generate Report** option was selected from the Autopsy interface.

The available report formats were displayed.

Possible report formats include:

* HTML Report
* Excel Report
* XLS
* Other supported reporting formats depending on the Autopsy version

📸 **Figure 12:** Selecting the report generation option.

---

## Step 2 — Configure Report

The required report module was selected.

The investigator can select the specific results or artifact categories that should be included in the report.

Examples include:

* Accounts
* Web Artifacts
* E-mail Messages
* Images
* Documents
* Deleted Files
* Hash Information
* File System Information
* Tagged Results

The report was then generated.

📸 **Figure 13:** Selecting and configuring forensic report contents.

---

## Step 3 — Review the Generated Report

The generated report was opened and reviewed.

The report provides documented forensic findings obtained during the examination.

It can be used to preserve and communicate the results of the investigation.

📸 **Figure 14:** Generated Autopsy forensic investigation report.

---

# 🔎 Forensic Findings & Analysis

The investigation demonstrated that Autopsy can process a forensic disk image and organize the extracted information into categories useful for digital forensic examination.

The following forensic areas were examined:

| Category         | Analysis                                      |
| ---------------- | --------------------------------------------- |
| Case Information | Case number and examiner information          |
| Evidence Source  | `4Dell Latitude CPi.E01` disk image           |
| File System      | Files and directory structure                 |
| Deleted Files    | Deleted artifacts identified by Autopsy       |
| File Types       | Categorization of files by type               |
| Metadata         | File properties and timestamps                |
| Hashes           | File identification and integrity information |
| Ingest Results   | Automatically processed forensic artifacts    |
| Reports          | Exported investigation results                |

---

# 🧠 Findings

* A dedicated forensic case was successfully created in Autopsy.
* Case information and examiner details were recorded.
* The provided `.E01` evidence image was successfully added as a data source.
* The associated `.E02` image segment was maintained with the `.E01` file.
* Autopsy Ingest Modules were configured to process the evidence.
* The file system and available forensic artifacts were examined.
* Deleted files and categorized file types were reviewed.
* Individual files could be examined for metadata and other forensic information.
* A forensic report was generated from the processed investigation results.

---

# 🛡️ Forensic Investigation Significance

Autopsy provides an organized workflow for conducting digital forensic investigations.

The use of a forensic disk image allows investigators to analyze an acquired copy of digital evidence rather than directly working on the original storage device.

The case-based structure helps maintain investigation information, while Ingest Modules automate the identification and categorization of potentially relevant artifacts.

The resulting reports provide a documented record of the analysis performed during the investigation.

---

# 📊 Result

✅ **Experiment Successfully Completed**

A new forensic case was successfully created in **Autopsy**, and the provided `4Dell Latitude CPi.E01` disk image was imported as a forensic data source.

The associated evidence was processed using Autopsy Ingest Modules, and the available file-system information, deleted files, file types, metadata, and other forensic artifacts were examined.

A forensic investigation report was subsequently generated from the analyzed evidence.

---

# 📝 Conclusion

The experiment demonstrated the practical use of **Autopsy Digital Forensics Platform** for conducting a basic digital forensic investigation.

A forensic case was created with appropriate case and examiner information, followed by the import of a segmented `.E01` disk image.

Autopsy's Ingest Modules were used to automatically process the evidence and identify potentially relevant digital artifacts.

The experiment provided practical experience in forensic case management, evidence import, artifact analysis, deleted-file examination, metadata analysis, and forensic reporting.
