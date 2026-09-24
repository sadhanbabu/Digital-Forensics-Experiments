# 🧪 EXPERIMENT 02 — Recover Deleted or Damaged Files Using TestDisk

---

## 🎯 Objective

To recover deleted files and repair a missing or corrupted partition from a storage device using the **TestDisk data recovery utility**.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows OS
* **Forensic Tool:** TestDisk v7.3-WIP Data Recovery Utility
* **Hardware:** Target storage device
* **Example Storage Device:** hp v221w 16GB USB Device

---

## 📋 Experiment Scenario

A storage device containing lost partitions and deleted files was examined using TestDisk.

TestDisk was used to analyze the physical storage device, examine its partition structure, search for lost partitions, locate deleted files, and recover selected files to a local destination.

TestDisk can be used to recover lost partitions and make certain non-booting disks accessible again when the problem is related to software errors, certain types of viruses, or human error such as accidental deletion of a partition table.

It can also be used to undelete files from supported file systems such as **FAT, exFAT, NTFS, and ext2**.

---

# ⚙️ Procedure

## Step 1 — Log Creation and Disk Selection

TestDisk was launched using the `testdisk_win.exe` application with administrator privileges.

When TestDisk started, the **[Create]** option was selected to create a log file containing technical information and messages generated during the operation.

After creating the log, the connected storage devices were displayed.

The target physical storage device containing the lost partitions or deleted files was selected using the arrow keys.

---

## Step 2 — Partition Table Type Selection

TestDisk displayed the available partition table types.

The appropriate partition table type was selected.

TestDisk can automatically detect the partition table type, so the default option is generally used when it correctly identifies the structure of the target disk.

The selected partition table type was then confirmed.

---

## Step 3 — Analyze the Current Partition Structure

The **[Analyse]** option was selected from the TestDisk main menu.

This option examines the current partition structure and searches for lost partitions.

The displayed partition structure was examined for:

* Missing partitions
* Partition errors
* Invalid NTFS boot information
* Missing logical partitions

The **[Quick Search]** option was then selected to search for lost partitions.

---

## Step 4 — Perform a Deeper Search

If the required partition was not identified during the Quick Search, or if partitions appeared with a deleted status, the **[Deeper Search]** option was used.

The Deeper Search performs a more extensive scan of the storage device.

It examines disk cylinders and searches for information such as:

* FAT32 backup boot sectors
* NTFS backup boot sectors
* Other partition-related structures

The partitions discovered during the search were reviewed.

Where necessary, the partition status could be changed using the arrow keys before proceeding.

---

## Step 5 — Identify and Access the Required Partition

After the search was completed, the required partition was identified from the discovered partitions.

The appropriate partition was highlighted.

The **`p` key** was used to display the files contained within the selected partition.

This allowed the directory structure and available files to be examined before recovery.

---

## Step 6 — Recover Deleted Files

The files within the selected partition were displayed.

The directory structure was navigated using the arrow keys.

TestDisk identifies deleted file entries using **red text**.

The required deleted file was selected.

For example, a deleted file such as:

`images (1).jpg`

could be selected for recovery.

The **`c` key** was used to copy the selected file.

The **`C` key** can be used to copy all selected files.

---

## Step 7 — Select the Recovery Destination

After selecting the file for recovery, TestDisk prompted for a destination directory.

A suitable local destination folder was selected.

The destination was confirmed using the appropriate confirmation key.

TestDisk then copied the selected file to the specified destination.

A successful recovery is indicated by a confirmation message such as:

```text
Copy done! 1 ok, 0 failed
```

This indicates that the selected file was successfully copied to the recovery destination.

---

# 💽 Optional — Partition Table and Boot Sector Recovery

TestDisk also provides options for recovering a partition itself or repairing certain boot-sector problems.

After leaving the file listing, the partition selection screen can be accessed.

The partition status can be changed from:

* **D — Deleted**
* **L — Logical**
* **P — Primary**

If the correct partitions are displayed, the **[Write]** option can be used to write the recovered partition structure.

The operation is then confirmed as required.

If a boot sector is damaged, the **[Backup BS]** option can be used to copy the backup boot sector over the damaged boot sector.

After completing the operation, TestDisk can be exited and the computer restarted to access the restored partition data.

---

# 🔎 Observations

1. TestDisk detected the connected physical storage device.
2. The storage device's partition structure was analyzed.
3. Quick Search was used to search for lost partitions.
4. Deeper Search provided a more extensive search when required.
5. Located partitions could be examined before recovery.
6. Files inside a selected partition could be listed using the `p` key.
7. Deleted files were identified in the file listing.
8. Selected deleted files could be copied to a secure local destination.
9. TestDisk displayed a confirmation message after successful file recovery.
10. TestDisk also provided options for partition-table and boot-sector recovery.

---

# 🧠 Findings

* **Partition Recovery:** TestDisk can identify lost partitions by analyzing the partition structure of a storage device.
* **Deleted File Recovery:** Deleted files can be located and copied from supported file systems.
* **Deep Analysis:** Deeper Search can locate partition information that may not be detected during the initial Quick Search.
* **File Examination:** Investigators can view the contents of a discovered partition before selecting files for recovery.
* **Recovery Destination:** Recovered files can be copied to a separate local destination.
* **Partition Repair:** TestDisk provides options to restore partition status and write a recovered partition structure when appropriate.

---

# 📊 Result

✅ **Experiment Successfully Completed**

TestDisk was successfully used to analyze the physical storage device and its partition structure.

Lost partitions were identified through partition searching, and deleted files were located, selected, and copied to a local recovery destination.

---

# 📝 Conclusion

The experiment demonstrated the use of **TestDisk** for recovering deleted files and identifying lost partitions from a storage device.

The storage device was analyzed using Quick Search and, when required, Deeper Search. The contents of identified partitions were examined, deleted files were selected, and the required files were recovered to a local destination.

TestDisk also provides additional functionality for recovering partition structures and repairing certain boot-sector problems.

