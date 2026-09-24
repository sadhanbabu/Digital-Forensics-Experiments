
# 🧪 EXPERIMENT 08 — Steganography Analysis and Hidden Data Detection Using StegExpose

---

## 🎯 Objective

To conduct a steganalysis investigation of digital image evidence using the **StegExpose** command-line utility, analyze the statistical properties associated with **Least Significant Bit (LSB)** steganography, calculate quantitative suspicion scores, classify potentially suspicious images using a configured threshold, and generate a structured CSV report for forensic documentation.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows / Linux / macOS
* **Runtime Environment:** Java Runtime Environment (JRE)
* **Forensics Tool:** StegExpose
* **Execution Format:** Java `.jar` executable
* **Evidence Files:** Digital image files such as:

  * `.png`
  * `.jpg`
  * `.jpeg`
  * `.bmp`
* **Output Format:** CSV

---

## 📋 Experiment Scenario

Steganography is a technique used to conceal information inside another digital object, such as an image, audio file, or video.

**Steganalysis** is the process of examining digital media for statistical or structural characteristics that may indicate the presence of hidden information.

**StegExpose** is a steganalysis tool designed to detect potential hidden information in digital images.

The tool examines statistical properties associated with image data and produces a numerical **suspect score**.

The score can be compared against a configured threshold to assist with the forensic triage of potentially suspicious images.

The experiment focused on:

* Preparing the Java environment
* Verifying Java availability
* Executing StegExpose from the command line
* Scanning a directory containing image evidence
* Applying an LSB detection threshold
* Generating suspicion scores
* Classifying image files
* Exporting the analysis results to CSV
* Reviewing the generated forensic report

---

# ⚙️ Procedure

## Step 1 — Open Command Prompt

The Windows Command Prompt was opened with administrative privileges.

The Command Prompt was launched using:

```text
Run as administrator
```

This provided an elevated command-line environment for executing the forensic analysis.

📸 **Figure 1:** Opening Command Prompt with administrative privileges.

---

# 📁 Step 2 — Navigate to the Working Directory

The Command Prompt was used to navigate to the directory containing:

```text
StegExpose.jar
testFolder
```

The `testFolder` directory contained the image evidence files to be analyzed.

The working directory therefore contained the following structure:

```text
Working Directory
│
├── StegExpose.jar
│
├── testFolder
│   ├── image1.jpg
│   ├── image2.png
│   ├── image3.bmp
│   └── ...
│
└── report.csv
```

The Java runtime environment was then verified.

### Command

```text
java --version
```

This command was used to confirm that Java was installed and available through the system PATH.

📸 **Figure 2:** Navigating to the StegExpose working directory and verifying the Java installation.

---

# 🔍 Step 3 — Execute StegExpose Analysis

StegExpose was executed using its Java `.jar` file.

The target evidence directory was specified as:

```text
testFolder
```

The analysis was configured with:

* **Execution speed:** `default`
* **Detection threshold:** `0.2`
* **Output report:** `report.csv`

### Command Executed

```text
java -jar "StegExpose.jar" "testFolder" default 0.2 report.csv
```

The command instructed StegExpose to scan the images contained within `testFolder` and generate the analysis results in CSV format.

📸 **Figure 3:** Executing StegExpose from the command line and generating `report.csv`.

---

# 🧮 Step 4 — Analyze the Detection Score

StegExpose generated a numerical score for each analyzed image.

The score was used to assess whether the statistical properties of an image appeared suspicious according to the configured detection threshold.

The threshold used during the experiment was:

```text
0.2
```

The general interpretation used for the experiment was:

```text
Score ≤ 0.2  →  Not flagged by the configured threshold
Score > 0.2  →  Flagged as suspicious
```

A threshold-based classification is intended for **forensic triage**, rather than proving that hidden data definitely exists.

A flagged image requires further investigation using additional forensic techniques.

---

# 📄 Step 5 — Generate the CSV Report

After the StegExpose analysis completed, the results were written to:

```text
report.csv
```

The CSV report provided a structured representation of the analysis results.

The report could contain information such as:

* Image filename
* Detection score
* Classification/status
* Analysis result

📸 **Figure 4:** Generated `report.csv` containing StegExpose analysis results.

---

# 🔎 Step 6 — Review the Generated Report

The generated report was opened using a text editor or spreadsheet application.

The report could be opened directly from Command Prompt using:

```text
notepad report.csv
```

Alternatively, the file could be opened using Microsoft Excel.

The results were reviewed to verify that:

* The expected image files were analyzed.
* Detection scores were generated.
* Threshold-based classifications were recorded.
* The CSV report was correctly formatted.

📸 **Figure 5:** Reviewing the generated StegExpose CSV report.

---

# 🔬 Steganalysis Analysis

## 1. Image Batch Processing

StegExpose processed the image files contained within the specified evidence directory.

The batch-processing approach allowed multiple digital image artifacts to be examined during a single analysis operation.

---

## 2. LSB Statistical Analysis

The experiment focused on statistical characteristics associated with **Least Significant Bit (LSB)** steganography.

LSB steganography can hide information by modifying the least significant bits of image data.

Such modifications may alter statistical properties of an image.

Steganalysis tools such as StegExpose use statistical detection techniques to identify patterns that may be associated with hidden information.

---

## 3. Suspicion Score

Each analyzed image was assigned a numerical detection score.

The score was evaluated against the configured threshold:

```text
0.2
```

Images exceeding the configured threshold were flagged for further examination.

The score should be interpreted as a **detection/triage indicator**, not definitive proof of steganographic content.

---

## 4. Evidence Classification

The analysis results were organized according to the generated scores and threshold-based classification.

A suspicious classification indicates that the image should receive additional forensic attention.

Further investigation could include:

* Examining image metadata
* Comparing image properties
* Checking file structure
* Comparing original and suspected copies
* Examining unusual image characteristics
* Using additional steganalysis tools

---

# 📊 Forensic Findings & Analysis

## 1. Java Environment

The Java runtime environment was successfully verified using:

```text
java --version
```

This confirmed that Java was available for executing the StegExpose `.jar` application.

---

## 2. StegExpose Execution

The StegExpose application was successfully executed against:

```text
testFolder
```

using:

```text
default
```

execution speed and a detection threshold of:

```text
0.2
```

---

## 3. Image Analysis

The image files within the evidence directory were processed by StegExpose.

The tool generated detection scores for the analyzed images.

These scores were used for statistical steganalysis and forensic triage.

---

## 4. Threshold Analysis

The configured threshold was:

```text
0.2
```

Images whose calculated scores exceeded the configured threshold were identified as potentially suspicious and suitable for further examination.

The threshold-based result does not independently establish that an image contains hidden data.

---

## 5. CSV Report Generation

The analysis results were successfully compiled into:

```text
report.csv
```

The report provided a structured record of the image filenames, detection scores, and associated classifications.

---

# 🧠 Findings

* Java was successfully verified using the `java --version` command.
* StegExpose was successfully executed from the command line.
* The `testFolder` evidence directory was processed.
* Multiple image files could be analyzed in a batch.
* Statistical characteristics associated with LSB steganography were evaluated.
* A detection score was generated for each analyzed image.
* The configured detection threshold was **0.2**.
* Images exceeding the configured threshold were flagged for further forensic examination.
* The analysis results were successfully exported to `report.csv`.
* The generated CSV report was opened and reviewed for verification.

---

# 🛡️ Forensic Significance

Steganography can be used to conceal information inside apparently ordinary digital media.

Because hidden information may not be visible during normal image viewing, **steganalysis** provides a method for identifying images that exhibit statistical characteristics potentially associated with data hiding.

The workflow demonstrated in this experiment can be summarized as:

```text
Digital Image Evidence
        ↓
StegExpose
        ↓
Statistical / LSB Analysis
        ↓
Detection Score
        ↓
Threshold Comparison
        ↓
Potentially Suspicious Image
        ↓
CSV Report
        ↓
Further Forensic Examination
```

StegExpose therefore provides a useful **triage mechanism** for identifying images that may require more detailed investigation.

A positive detection should not by itself be treated as conclusive evidence of hidden data because statistical detection can produce false positives and requires appropriate interpretation.

---

# 📄 Evidence Report

The primary output generated during the experiment was:

```text
report.csv
```

The report was used to document:

* Analyzed image files
* Detection scores
* Threshold-based classifications
* Steganalysis results

The CSV format also allows the results to be easily opened in spreadsheet software for documentation and further analysis.

---

# 📊 Result

✅ **Experiment Successfully Completed**

The steganalysis experiment was successfully performed using **StegExpose**.

The tool scanned the image evidence contained within `testFolder`, analyzed statistical characteristics associated with potential LSB-based steganography, calculated detection scores, and evaluated the results against the configured threshold of **0.2**.

The analysis results were successfully exported to:

```text
report.csv
```

The generated report was reviewed to verify the analyzed files, detection scores, and classifications.

---

# 📝 Conclusion

The experiment demonstrated the practical application of **StegExpose** for digital image steganalysis.

The Java environment was verified, the StegExpose application was executed through the command line, and the image evidence directory was processed in batch.

The tool generated quantitative detection scores that were compared against a configured threshold of **0.2**. Images identified as potentially suspicious could then be selected for further forensic investigation.

The analysis results were automatically compiled into a structured CSV report, providing a convenient format for forensic documentation and reporting.

Overall, the experiment provided practical experience in **steganalysis, LSB-based statistical detection, suspicion-score analysis, threshold-based triage, batch image processing, and forensic report generation using StegExpose**.
