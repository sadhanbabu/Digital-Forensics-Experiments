
# 🧪 EXPERIMENT 07 — Android Mobile Forensics Using AFLogical OSE and ADB

---

## 🎯 Objective

To configure an Android mobile forensics environment, establish a secure **Android Debug Bridge (ADB)** connection, deploy and execute **AFLogical OSE** for logical data extraction, transfer the resulting forensic artifacts to a host workstation, and verify and analyze the extracted CSV data.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows / Linux / macOS
* **Forensics Tool:** AFLogical OSE (Open Source Edition)
* **Command-Line Utility:** Android Debug Bridge (ADB)
* **Runtime Environment:** Java Development Kit (JDK)
* **Hardware:** Android mobile device
* **Connection:** USB data cable
* **Output Format:** CSV (Comma-Separated Values)

---

## 📋 Experiment Scenario

Mobile devices contain important digital evidence such as contacts, SMS messages, call records, and other application-related information.

**AFLogical OSE**, developed by viaForensics, is an Android-based logical acquisition tool that can collect selected user artifacts from an Android device.

The tool works together with **Android Debug Bridge (ADB)** to establish communication between the forensic workstation and the Android device.

Logical extraction retrieves accessible information through the Android operating system and its data interfaces. Unlike physical acquisition, logical acquisition does not create a bit-by-bit copy of the device's storage.

The experiment focused on:

* Preparing an Android forensic environment
* Enabling Android Developer Options
* Enabling USB Debugging
* Establishing an ADB connection
* Verifying the connected device
* Installing AFLogical OSE
* Performing logical data extraction
* Extracting contacts, SMS, and call records
* Transferring evidence to the forensic workstation
* Verifying CSV artifacts
* Examining timestamps and extracted records
* Removing the forensic collection application after acquisition

---

# ⚙️ Procedure

## Step 1 — Environment Setup

The forensic workstation was prepared with the required Android forensic tools.

The following components were installed:

* Java Development Kit (JDK)
* Android SDK Platform-Tools
* Android Debug Bridge (ADB)
* AFLogical OSE APK

ADB was added to the system PATH so that the `adb` command could be executed from Command Prompt.

📸 **Figure 1:** Android forensic environment and ADB setup.

---

# 📱 Step 2 — Prepare the Android Device

The target Android device was prepared for forensic acquisition.

Developer Options were enabled by navigating to:

```text
Settings → About Phone → Build Number
```

The **Build Number** was tapped multiple times until Developer Options became available.

USB Debugging was then enabled from:

```text
Settings → Developer Options → USB Debugging
```

The Android device was connected to the forensic workstation using a USB data cable.

---

# 🔌 Step 3 — Verify ADB Connection

Command Prompt was opened on the forensic workstation.

The following command was executed:

```text
adb devices
```

### Command

```text
adb devices
```

The command displays Android devices detected by the ADB service.

A successfully authorized device should appear in the output.

Example:

```text
List of devices attached
XXXXXXXX    device
```

The `device` status indicates that ADB communication has been established and the device has been authorized for debugging.

📸 **Figure 2:** Terminal output showing the Android device successfully connected through ADB.

---

# 📦 Step 4 — Install AFLogical OSE

The `aflogical.apk` file was placed in an accessible directory on the forensic workstation.

The Command Prompt was navigated to the directory containing the APK.

The following command was executed:

```text
adb install aflogical.apk
```

### Command

```text
adb install aflogical.apk
```

ADB transferred and installed the AFLogical OSE application onto the Android device.

A successful installation was indicated by the appropriate ADB installation confirmation.

📸 **Figure 3:** Successful installation of the AFLogical OSE APK.

---

# 📲 Step 5 — Launch AFLogical OSE

After installation, the AFLogical OSE application was launched from the Android device.

The application provided options for selecting the categories of information to be collected.

The relevant forensic artifacts were selected for extraction.

Examples include:

* Contacts
* SMS messages
* Call logs
* MMS messages
* Other supported logical artifacts

The extraction process was then initiated.

📸 **Figure 4:** AFLogical OSE interface showing available data categories and extraction options.

---

# 📥 Step 6 — Perform Logical Data Extraction

AFLogical OSE queried the accessible Android data sources and collected the selected information.

The extracted records were organized into CSV files.

The extraction directory on the Android device was:

```text
/sdcard/aflogical
```

The generated artifacts included files such as:

```text
contacts.csv
sms.csv
calls.csv
```

The exact files produced may depend on the Android version, device configuration, and artifacts selected during the acquisition.

📸 **Figure 5:** AFLogical OSE extraction process and generated forensic artifacts.

---

# 💻 Step 7 — Transfer Evidence to the Host Workstation

The extracted forensic artifacts were transferred from the Android device to the forensic workstation.

A dedicated evidence directory was created:

```text
C:\DF\AFLogical_Evidence\
```

The extracted CSV files were stored in this directory for further examination.

The evidence directory contained artifacts such as:

```text
contacts.csv
sms.csv
calls.csv
```

📸 **Figure 6:** Transferred AFLogical OSE evidence files on the forensic workstation.

---

# 🔎 Step 8 — Verify and Analyze Extracted Evidence

The generated CSV files were opened using spreadsheet software or a text editor.

The extracted records were examined to verify that the acquisition produced structured and readable data.

The analysis focused on:

* Contact names
* Telephone numbers
* SMS information
* Call information
* Dates and times
* Direction of communication
* Available metadata
* Record structure

The original extracted files were preserved, and analysis was performed on copies where appropriate.

📸 **Figure 7:** Examining extracted contacts, SMS records, and call logs in spreadsheet format.

---

# 🕒 Timestamp Analysis

The timestamps contained within mobile forensic artifacts were examined during analysis.

Mobile applications and databases may represent timestamps using formats such as:

* Unix Epoch time
* Unix Epoch milliseconds
* UTC
* Device-local time

For example, Unix Epoch timestamps represent time relative to:

```text
January 1, 1970 00:00:00 UTC
```

Therefore, investigators should identify the timestamp format before interpreting dates and times.

Timestamp conversion should also consider the device's configured timezone and the timezone used by the application or database.

📸 **Figure 8:** Examination of timestamp fields within the extracted CSV evidence.

---

# 🧹 Step 9 — Forensic Cleanup

After the acquisition and verification process was completed, the AFLogical OSE application was removed from the Android device.

The following ADB command was used:

```text
adb uninstall com.viaforensics.android.aflogical
```

### Command

```text
adb uninstall com.viaforensics.android.aflogical
```

The device was then safely disconnected from the forensic workstation.

📸 **Figure 9:** Successful removal of the AFLogical OSE application.

---

# 🔎 Forensic Findings & Analysis

## 1. ADB Bridge Communication

The ADB service successfully detected and communicated with the Android device.

The device appeared in the output of:

```text
adb devices
```

This confirmed that the required ADB communication and device authorization were established.

---

## 2. AFLogical OSE Deployment

The AFLogical OSE APK was successfully installed on the Android device using:

```text
adb install aflogical.apk
```

The application was then launched directly on the target device.

---

## 3. Logical Artifact Extraction

AFLogical OSE successfully performed logical extraction of selected accessible Android artifacts.

The extracted information was organized into structured CSV files.

Examples included:

```text
contacts.csv
sms.csv
calls.csv
```

---

## 4. Evidence Transfer

The generated CSV artifacts were transferred to the forensic workstation and stored in:

```text
C:\DF\AFLogical_Evidence\
```

This provided a dedicated location for examination and documentation of the extracted evidence.

---

## 5. Data Integrity Verification

The extracted CSV files were opened and examined to verify:

* File accessibility
* Record structure
* Field values
* Timestamps
* Contact information
* Communication records

The extracted records were available in a structured format suitable for further forensic analysis and reporting.

---

## 6. Timestamp Examination

The timestamp fields were examined to understand how the mobile device represented dates and times.

The analysis demonstrated the importance of identifying whether timestamps were represented as:

```text
Unix Epoch
Unix Epoch milliseconds
UTC
Device-local time
```

Correct timestamp interpretation is important when reconstructing communication events.

---

# 🧠 Findings

* The Android forensic environment was successfully configured.
* Developer Options and USB Debugging were enabled on the target device.
* ADB successfully detected and communicated with the Android device.
* AFLogical OSE was successfully installed using ADB.
* Logical extraction was performed using the AFLogical OSE application.
* Selected mobile artifacts were extracted into structured CSV files.
* Contacts, SMS, and call-log artifacts were examined.
* The extracted evidence was transferred to the forensic workstation.
* CSV artifacts were verified for readability and record structure.
* Timestamp fields were examined for forensic interpretation.
* AFLogical OSE was removed from the device after the acquisition process.

---

# 🛡️ Forensic Significance

Logical mobile acquisition provides investigators with a method for collecting accessible user data from an operating Android device.

The workflow demonstrated in this experiment can be summarized as:

```text
Android Device
      ↓
Enable USB Debugging
      ↓
ADB Connection
      ↓
Install AFLogical OSE
      ↓
Select Artifacts
      ↓
Logical Extraction
      ↓
CSV Evidence
      ↓
Transfer to Forensic Workstation
      ↓
Verification & Analysis
      ↓
Reporting
```

This process demonstrates how mobile forensic investigators can collect structured artifacts such as contacts, messages, and call records for further examination.

Logical acquisition does not necessarily recover deleted data or provide a complete physical image of the device. Its results are therefore dependent on the data accessible through the Android operating system and the capabilities of the acquisition tool.

---

# 📊 Result

✅ **Experiment Successfully Completed**

The Android device was successfully connected to the forensic workstation using **Android Debug Bridge (ADB)**.

AFLogical OSE was installed and used to perform a logical acquisition of selected mobile artifacts.

Contacts, SMS messages, and call-log information were extracted into structured CSV files, transferred to the forensic workstation, and examined for data integrity and timestamp information.

The extracted artifacts were successfully prepared for forensic analysis and documentation.

---

# 📝 Conclusion

The experiment demonstrated the practical use of **ADB and AFLogical OSE** for Android mobile logical acquisition.

The Android device was configured for forensic communication by enabling USB Debugging, after which ADB was used to establish and verify the connection.

AFLogical OSE was deployed to the device and used to extract accessible user artifacts such as contacts, SMS messages, and call records.

The extracted CSV files were transferred to the forensic workstation and examined for record structure, metadata, and timestamp information.

The experiment provided practical experience in **Android device preparation, ADB communication, logical mobile acquisition, forensic artifact extraction, evidence transfer, timestamp analysis, and forensic documentation**.
