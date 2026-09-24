
# 🧪 EXPERIMENT NO. 10 — Malware Disassembly and Code Analysis Using Ghidra

## 🎯 Objective

To set up a secure analysis environment and use **Ghidra** for reverse engineering, disassembly, and decompilation of binary code.

The experiment focuses on:

* Importing and analyzing executable binaries
* Disassembling machine code into assembly instructions
* Extracting hardcoded strings
* Identifying imported libraries and functions
* Decompiling assembly into C-like pseudocode
* Understanding program execution flow
* Analyzing stripped binaries
* Identifying potential indicators of compromise (IOCs) and suspicious behaviors

> **Note:** The analysis should be performed using a benign sample or controlled test binary inside an isolated virtual machine. The sample used in this experiment was analyzed statically rather than executed as malware.

---

## 🧰 Tools / Requirements

| Requirement              | Details                                |
| ------------------------ | -------------------------------------- |
| Operating System         | Isolated Windows/Linux Virtual Machine |
| Reverse Engineering Tool | Ghidra                                 |
| Runtime Environment      | Java Development Kit (JDK)             |
| Sample                   | Benign / Controlled Test Binary        |
| Binary Format            | ELF Linux executable                   |
| Analysis Type            | Static Analysis                        |

---

## 📋 Experiment Scenario

Malware analysts often need to investigate executable programs without having access to their original source code.

A compiled program contains machine instructions that are difficult to understand directly.

Ghidra helps bridge this gap:

```text
Binary File
     ↓
Disassembly
     ↓
Assembly Instructions
     ↓
Function Analysis
     ↓
Decompiler
     ↓
C-like Pseudocode
     ↓
Behavioral Understanding
```

Ghidra's **CodeBrowser** provides several useful views, including:

* Listing / assembly instructions
* Symbol Tree
* Defined Strings
* Imports
* Functions
* Decompiler
* Function Graph

These features allow investigators to understand the structure and execution logic of a binary.

---

# ⚙️ Procedure

## Step 1 — Install Ghidra and Create a Project

### 1.1 Download Ghidra

1. Open a web browser.
2. Search for the official **Ghidra** repository/download page.
3. Download the Ghidra ZIP archive.
4. Extract the ZIP file.
5. Launch Ghidra.
6. Accept the required terms and license agreement if prompted.

Ghidra requires a compatible **JDK** to run.

---

### 1.2 Create a New Project

1. Open Ghidra.
2. Select:

```text
File
 ↓
New Project
```

3. Select a **non-shared project**.
4. Create the project with the name:

```text
Ghidra_Malware_Analysis
```

5. Select an appropriate project directory.

---

### 1.3 Import the Binary

1. Navigate to:

```text
File
 ↓
Import File
```

2. Select the target binary.
3. Continue with the default import configuration.
4. Confirm the imported file appears inside the project.

📸 **Figure 1: Initial Ghidra Project Window showing the newly imported binary**

---

### 1.4 Open the Binary in CodeBrowser

1. Double-click the imported binary.
2. Ghidra opens the file in **CodeBrowser**.
3. When prompted, select:

```text
Auto Analyze
```

4. Allow Ghidra to perform the initial automated analysis.

The analysis identifies functions, references, instructions, strings, symbols, and other binary structures.

📸 **Figure 2: Ghidra CodeBrowser interface displaying the disassembly after Auto-Analysis**

---

# 🔎 Step 2 — String Extraction and Import Analysis

## 2.1 Extract Defined Strings

Strings embedded inside a binary can provide useful information about its functionality.

Navigate to:

```text
Window
 ↓
Defined Strings
```

Ghidra displays strings identified within the binary.

Examples of potentially useful strings include:

```text
File paths
Error messages
URLs
Command names
Library names
Configuration values
```

In malware analysis, strings may provide clues about:

* Network communication
* Files accessed by the program
* Commands executed
* Encryption-related functionality
* Persistence mechanisms
* Error messages
* Configuration information

📸 **Figure 3: Defined Strings extracted from the binary**

---

## 2.2 Analyze Imported Libraries

In the **Symbol Tree** pane:

```text
Imports
```

Expand the Imports directory.

The experiment identified a dependency on:

```text
libc.so.6
```

`libc.so.6` is a standard Linux C library and is commonly used by normal Linux applications.

Imported libraries are useful during malware analysis because they can provide clues about what capabilities a program may use.

For example, imports associated with:

```text
Networking
File operations
Process creation
Encryption
System calls
```

may help investigators understand the functionality of an unknown program.

---

# 🧠 Step 3 — Function Decompilation

## 3.1 Locate Functions

In the **Symbol Tree**:

```text
Functions
```

Expand the directory to view functions identified by Ghidra.

Locate the program's entry function.

---

## 3.2 Examine Assembly Instructions

Select the identified function.

The **Listing** window displays the low-level assembly instructions.

Example structure:

```text
Instruction
    ↓
Register Operations
    ↓
Memory Operations
    ↓
Function Calls
    ↓
Conditional Branches
```

Assembly instructions represent operations performed by the processor.

---

## 3.3 Examine Decompiled Code

The **Decompiler** window translates the assembly instructions into C-like pseudocode.

This makes the program's logic easier for investigators to understand.

The analysis showed the entry function leading to:

```text
__libc_start_main
```

This is an important part of the Linux program startup sequence.

📸 **Figure 4: Decompiled C-like pseudocode of the entry function**

---

# 🔬 Step 4 — Execution Flow Visualization

## 4.1 Identify the Actual Main Function

The analyzed binary was **stripped**, meaning original symbol information such as developer-defined function names was removed.

As a result, the original:

```text
main()
```

function name was not directly available.

The execution flow was therefore traced through:

```text
entry function
       ↓
__libc_start_main
       ↓
main function pointer
       ↓
actual program logic
```

The first parameter passed to `__libc_start_main` was examined to identify the actual main execution routine.

The analysis resolved the main routine as:

```text
FUN_00104c00
```

---

## 4.2 Open the Function Graph

After navigating to:

```text
FUN_00104c00
```

open the function graph:

```text
Window
 ↓
Function Graph
```

The Function Graph represents the program's control flow using nodes and connecting arrows.

It helps visualize:

* Function execution
* Conditional branches
* Loops
* Decision points
* Different execution paths

📸 **Figure 5: Visual Function Graph illustrating the execution flow of the stripped main function**

---

# 🔎 Forensic Findings & Analysis

## 1. Binary Structure Analysis

Ghidra successfully analyzed the ELF binary and exposed important structural information, including:

* Binary architecture
* Code sections
* Data sections
* Metadata
* Functions
* Program entry information

This provided the initial understanding of the binary before examining its individual functions.

---

## 2. Strings and Imports

The Defined Strings window was used to identify hardcoded strings.

The Imports section showed:

```text
libc.so.6
```

The use of a standard Linux library was consistent with the analyzed benign Linux utility.

In a malware investigation, imported libraries and functions could provide indicators of capabilities such as:

```text
Network communication
File manipulation
Process creation
Encryption
System interaction
```

Therefore, imports are useful for developing an initial behavioral profile.

---

## 3. Decompilation Analysis

Ghidra's Decompiler successfully converted low-level assembly instructions into C-like pseudocode.

The analysis highlighted:

```text
__libc_start_main
```

which is involved in the startup process of a Linux executable.

The decompiled representation made the program's control flow easier to understand compared with examining raw assembly alone.

---

## 4. Control Flow Analysis

The **Function Graph** provided a visual representation of the program's execution structure.

The graph displayed:

```text
Basic Block
     ↓
Condition
   ↙   ↘
Path A  Path B
   ↓      ↓
More Instructions
```

This makes complicated functions easier to investigate because branches and loops can be followed visually.

---

## 5. Stripped Binary Analysis

The analyzed binary had its symbol information stripped.

The original symbol table:

```text
.symtab
```

was unavailable.

Therefore, original developer-defined function names and variable names were not directly available.

The execution entry point was instead analyzed by tracing the parameter passed to:

```text
__libc_start_main
```

This allowed the actual main routine to be resolved as:

```text
FUN_00104c00
```

This demonstrates how reverse engineers can recover useful program structure even when symbol information has been removed.

---

# 🧠 Key Findings

| Investigation Area | Finding                                           |
| ------------------ | ------------------------------------------------- |
| Binary Format      | ELF executable                                    |
| Analysis Type      | Static analysis                                   |
| Tool               | Ghidra                                            |
| Code Analysis      | Successful disassembly                            |
| Strings            | Defined strings extracted                         |
| Imports            | `libc.so.6` identified                            |
| Decompiler         | C-like pseudocode generated                       |
| Startup Function   | `__libc_start_main` identified                    |
| Symbol Information | Binary was stripped                               |
| Main Function      | Resolved as `FUN_00104c00`                        |
| Flow Analysis      | Function Graph successfully generated             |
| Binary Assessment  | Consistent with the analyzed benign Linux utility |

---

# 🛡️ Forensic Significance

Ghidra is useful in digital forensics and malware analysis because it allows investigators to examine executable files without requiring the original source code.

Important capabilities include:

### 🔹 Disassembly

Converts machine-code instructions into assembly instructions.

### 🔹 Decompilation

Converts assembly into C-like pseudocode to make program logic easier to understand.

### 🔹 String Analysis

Can reveal useful information embedded inside executable files.

### 🔹 Import Analysis

Helps identify external libraries and functions used by a program.

### 🔹 Function Analysis

Allows investigators to study individual functions and their relationships.

### 🔹 Control Flow Analysis

Function Graphs help visualize branches, loops, and execution paths.

### 🔹 Stripped Binary Analysis

Investigators can trace execution paths even when original function names and symbol information have been removed.

---

# 📊 Result

Ghidra was successfully used to **disassemble, decompile, and analyze the target ELF binary**.

The experiment successfully demonstrated:

* Binary importing
* Automated analysis
* Disassembly
* String extraction
* Import analysis
* Function identification
* C-like decompilation
* Control-flow visualization
* Stripped-binary analysis
* Identification of the main execution routine

The analysis resolved the main routine as:

```text
FUN_00104c00
```

and identified its relationship with:

```text
__libc_start_main
```

The analyzed binary exhibited characteristics consistent with the controlled benign Linux utility used in the experiment.

---

# 📝 Conclusion

The experiment successfully demonstrated the use of **Ghidra for static malware and binary analysis**.

The binary was imported into a Ghidra project, automatically analyzed, disassembled, and decompiled. Defined strings and imported libraries were examined to understand the binary's dependencies and potential functionality.

The Decompiler and Function Graph provided higher-level representations of the program's logic, while analysis of the stripped symbol information demonstrated how investigators can trace execution and identify the main routine even when original function names have been removed.

Overall, Ghidra provides a powerful framework for **reverse engineering, static malware analysis, executable investigation, and identification of potential indicators of compromise**.
