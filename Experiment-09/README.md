
# 🧪 EXPERIMENT NO. 09 — Identifying Suspicious Processes and Malware Analysis Using Sysinternals Process Explorer

## 🎯 Objective

To conduct an in-depth behavioral and structural analysis of active Windows operating system processes using **Sysinternals Process Explorer**.

The experiment focuses on:

* Analyzing **parent-child process relationships**
* Investigating **process IDs (PIDs)** and resource usage
* Verifying **digital signatures**
* Checking **process execution paths**
* Inspecting **network connections**
* Analyzing **loaded DLLs**
* Using **VirusTotal** for threat-intelligence verification
* Identifying suspicious, unauthorized, or masquerading processes
* Suspending or terminating confirmed malicious processes
* Performing a post-mitigation system scan

---

## 🧰 Tools / Requirements

| Requirement         | Details                                        |
| ------------------- | ---------------------------------------------- |
| Operating System    | Windows OS                                     |
| Forensics Tool      | Sysinternals Process Explorer                  |
| Threat Intelligence | VirusTotal / ProcessLibrary                    |
| Security Scanner    | Windows Defender / Malwarebytes                |
| Privileges          | Administrator privileges                       |
| Internet            | Required for online threat-intelligence lookup |

---

## 📋 Experiment Scenario

A Windows system may contain hundreds of active processes. Some are legitimate operating-system components, while others may belong to applications, background services, or potentially malicious software.

Attackers may also use **masquerading**, where a malicious executable is given a name similar to a legitimate Windows process.

For example:

```text
Legitimate:
C:\Windows\System32\lsass.exe

Potentially suspicious:
C:\Users\<User>\AppData\Local\Temp\lsass.exe
```

Therefore, process names alone should not be treated as proof of legitimacy.

**Process Explorer** provides additional information such as:

* Parent and child processes
* Process ID
* CPU and memory usage
* Executable path
* Digital signatures
* Network connections
* Loaded DLLs
* Process properties
* Cryptographic hashes
* VirusTotal reputation

This allows a forensic investigator to examine suspicious processes systematically.

---

# ⚙️ Procedure

## Step 1 — Download and Initialize Process Explorer

1. Download **Sysinternals Process Explorer** from the official Microsoft Sysinternals collection.
2. Extract the downloaded archive.
3. Open the extracted folder.
4. Locate:

```text
procexp64.exe
```

5. Right-click the executable.
6. Select:

```text
Run as Administrator
```

Administrator privileges provide greater visibility into system-level processes and process attributes.

📸 **Figure 1: Launching Process Explorer with administrative privileges**

---

## Step 2 — Familiarize with the Process Explorer Interface

After launching Process Explorer, observe the main process tree.

The interface displays information such as:

* Process name
* Process ID (PID)
* CPU usage
* Memory usage
* Description
* Company name
* Parent-child relationships

The process tree helps investigators understand **which process started another process**.

Example:

```text
services.exe
 ├── svchost.exe
 │    ├── Service Process
 │    └── Service Process
 └── Other Services
```

Process Explorer also uses different colors to indicate process states.

Examples from the experiment:

| Color      | Meaning                   |
| ---------- | ------------------------- |
| Pink       | Suspended processes       |
| Light Blue | User processes            |
| Dark Blue  | System services           |
| Green      | Newly spawned processes   |
| Red        | Recently exited processes |

📸 **Figure 2: Process Explorer dashboard displaying hierarchical process trees and resource metrics**

---

# 🔎 Step 3 — Investigate Suspicious Processes

Processes that appear unfamiliar, consume unusually high resources, or have suspicious characteristics should be investigated further.

### 3.1 Verify Digital Signatures

1. Right-click the suspicious process.
2. Select:

```text
Properties
```

3. Open the **Image** tab.
4. Examine the digital signature information.

A legitimate Windows executable may contain a valid Microsoft digital signature.

Check:

```text
Publisher / Company
Digital Signature
Image Path
```

A missing or invalid signature can be treated as a **suspicious indicator**, but it does not automatically prove that the process is malware.

📸 **Figure 3: Inspecting image properties, cryptographic signatures, and execution file paths**

---

### 3.2 Check the Execution Path

Inspect the executable's location under the **Image** tab.

Legitimate Windows system executables commonly exist in locations such as:

```text
C:\Windows\System32
```

A process with a familiar system-process name executing from an unusual location should be investigated carefully.

Example:

```text
Expected:
C:\Windows\System32\lsass.exe

Suspicious example:
C:\Users\<User>\AppData\Local\Temp\lsass.exe
```

The location alone is not conclusive; the investigator should correlate it with signatures, hashes, parent process, and other evidence.

---

### 3.3 Inspect Network Activity

Open the suspicious process's properties and examine its network-related information.

Look for:

* Unexpected external connections
* Remote IP addresses
* TCP connections
* Unusual network activity
* Connections that do not match the expected function of the process

Network activity should be correlated with the process's purpose before deciding whether it is suspicious.

---

### 3.4 Inspect Loaded DLLs

Process Explorer can display the Dynamic Link Libraries (**DLLs**) loaded by a selected process.

Open:

```text
View
   ↓
Lower Pane View
   ↓
DLLs
```

Alternatively, use:

```text
Ctrl + D
```

Select a process in the upper pane.

The lower pane will display DLLs loaded by that process.

Investigate DLLs with characteristics such as:

* Unusual file paths
* Missing company information
* Unexpected publishers
* Suspicious locations
* Libraries that do not appear relevant to the process

Unexpected DLL loading can be an indicator requiring further investigation.

---

# 🌐 Step 4 — Threat Intelligence Lookup

If a process appears anomalous, investigate its reputation using online threat-intelligence services.

Examples:

* VirusTotal
* ProcessLibrary

The investigator can search using the **process hash** rather than relying only on the filename.

Example suspicious filename:

```text
randomname123.exe
```

The investigation can include:

```text
Process
   ↓
Executable
   ↓
Hash
   ↓
Threat Intelligence Database
   ↓
Detection Results
```

A hash allows the investigator to compare the exact executable against known malware and security-vendor databases.

📸 **Figure 4: Querying process hashes against online malware repositories**

---

## 🛡️ Step 5 — Mitigation and Containment

If a process is confirmed malicious or needs to be stopped because it is unresponsive:

1. Right-click the process.
2. Select:

```text
Suspend
```

to temporarily stop its execution.

Or select:

```text
Kill Process
```

to terminate the process.

After termination, identify the executable using its verified image path.

The file can then be handled according to the organization's incident-response or forensic procedures.

> **Forensic note:** A suspicious process should be investigated and its evidence documented before termination whenever possible, because terminating a process can change volatile evidence.

📸 **Figure 5: Suspending or terminating a suspicious process**

---

# 🔐 Step 6 — Perform a Comprehensive System Scan

After mitigation, perform a full system scan using a trusted security tool.

For example:

```text
Windows Defender
```

or another authorized anti-malware solution.

The purpose is to check for:

* Remaining malicious files
* Additional malware
* Persistence mechanisms
* Related malicious components
* Other compromised files

📸 **Figure 6: Performing a post-mitigation system scan using Windows Defender**

---

# 🔎 Forensic Findings & Analysis

## 1. Process Hierarchy and Lineage

Legitimate Windows processes such as:

```text
lsass.exe
winlogon.exe
services.exe
```

can be examined through their parent-child relationships.

The experiment observed legitimate system processes executing from trusted system locations such as:

```text
C:\Windows\System32
```

and displaying valid Microsoft digital signatures.

Parent-child relationships were also examined to determine whether process creation followed expected operating-system behavior.

---

## 2. Digital Signature Verification

Digital signatures were examined through the process properties.

A valid signature from a trusted publisher provides evidence supporting the authenticity of an executable.

However:

```text
Valid Signature ≠ Automatically Safe
```

and:

```text
No Signature ≠ Automatically Malware
```

Signature information should therefore be combined with other forensic indicators.

---

## 3. Execution Path Analysis

The executable location was examined to detect potential masquerading.

For example:

```text
C:\Windows\System32\lsass.exe
```

would be consistent with the expected location of the Windows system executable.

A similarly named executable running from a temporary or unexpected user directory would require additional investigation.

---

## 4. Threat Intelligence Analysis

VirusTotal integration was used for automated hash-based reputation checking.

According to the experiment observations:

```text
Clean binaries:
0/72 detections
```

while anomalous binaries were observed with higher detection ratios across multiple security vendors.

These results should be interpreted as **threat-intelligence evidence**, not as the sole basis for a forensic conclusion.

📸 **Figure 7: VirusTotal hash reputation results**

---

## 5. Network Activity Correlation

Suspicious processes were also examined for outbound TCP/IP connections.

Anomalous processes in the experiment exhibited unexpected outbound connections to external systems.

The investigator should correlate:

```text
Process
   ↓
Executable Path
   ↓
Hash
   ↓
Network Connection
   ↓
Threat Intelligence
```

to build a stronger assessment of the process.

---

# 🧠 Key Findings

| Investigation Area  | Finding                                                       |
| ------------------- | ------------------------------------------------------------- |
| Process Hierarchy   | Parent-child process relationships were examined              |
| Process Identity    | Process names and PIDs were analyzed                          |
| Digital Signature   | System-process signatures were checked                        |
| Execution Path      | Executable locations were inspected                           |
| DLL Analysis        | Loaded DLLs were examined                                     |
| Network Activity    | TCP/IP connections were investigated                          |
| Threat Intelligence | Process hashes were checked against online databases          |
| Malware Detection   | Anomalous binaries could be correlated with detection results |
| Mitigation          | Suspicious processes could be suspended or terminated         |
| Post-Mitigation     | Full system security scan was performed                       |

---

# 🛡️ Forensic Significance

Process Explorer is useful in live-system forensic investigations because it provides visibility into the **current state of the operating system**.

It can help investigators identify:

* Process masquerading
* Suspicious process creation
* Unusual parent-child relationships
* Unsigned or unexpectedly signed executables
* Suspicious execution locations
* Unexpected DLL loading
* Unauthorized network connections
* Potential malware activity

A strong investigation should combine multiple indicators rather than relying on a single characteristic such as the process name.

---

# 📊 Result

Sysinternals Process Explorer was successfully used to:

* Monitor active Windows processes
* Examine hierarchical process relationships
* Verify digital signatures
* Inspect executable paths
* Analyze loaded DLLs
* Examine network activity
* Perform hash-based threat-intelligence checks
* Identify suspicious or unauthorized process characteristics
* Suspend or terminate processes when required
* Perform post-mitigation system scanning

The experiment demonstrated how Process Explorer can support **live process investigation and malware analysis** on a Windows system.

---

# 📝 Conclusion

The experiment successfully demonstrated the use of **Sysinternals Process Explorer** for live Windows process investigation.

Process hierarchy, execution paths, digital signatures, DLLs, network connections, and threat-intelligence results were examined to distinguish legitimate processes from potentially suspicious activity.

The experiment also demonstrated the importance of correlating multiple forensic indicators before classifying a process as malicious. Process Explorer therefore provides valuable visibility for **process monitoring, malware investigation, and live-system forensic analysis**.
