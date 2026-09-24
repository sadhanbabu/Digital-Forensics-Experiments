# 🧪 EXPERIMENT 01 — Evidence Acquisition Using FTK Imager

---

## 🎯 Objective

To acquire digital evidence from a storage device using **AccessData FTK Imager**, create a forensic disk image, record the required evidence information, and verify the integrity of the acquired image using cryptographic hash values.

---

## 🧰 Tools / Requirements

* **Forensic Software:** AccessData FTK Imager
* **Operating System:** Windows OS
* **Evidence Device:** USB storage device
* **Forensic Image Formats:** Raw (dd), E01, SMART, or AFF
* **Evidence Storage:** A designated destination folder for the forensic image

---

## 📋 Experiment Scenario

A storage device was selected as the source of digital evidence for forensic acquisition.

The purpose of the experiment was to create a forensic image of the source device using FTK Imager while maintaining the integrity of the original evidence.

The acquired image was subsequently verified using cryptographic hash values.

---

## 💾 Evidence / Input

* **Evidence Type:** Storage device
* **Source:** Target USB storage device
* **Device:** hp v221w 16GB USB Device
* **Acquisition Tool:** AccessData FTK Imager
* **Output:** Forensic disk image

---

# ⚙️ Procedure

## Step 1 — Launch FTK Imager

FTK Imager was launched on the Windows system to begin the forensic acquisition process.

The application was used to access the target storage device and create its forensic image.

---

## Step 2 — Open Create Disk Image

The **Create Disk Image** option was selected from FTK Imager.

This can be accessed through:

**File → Create Disk Image**

The corresponding toolbar option can also be used.

---

## Step 3 — Select Evidence Source

The appropriate source evidence type was selected.

The available source types include:

* Physical Drive
* Logical Drive

The target storage device was then selected for acquisition.

---

## Step 4 — Select the Target Drive

The target USB storage device was selected from the available drives.

The selected device was used as the source for creating the forensic image.

---

## Step 5 — Select Image Type

The **Add** option was used to configure the destination forensic image.

FTK Imager provides several image formats, including:

* **Raw (dd)**
* **E01**
* **SMART**
* **AFF**

The required image format was selected for the acquisition.

---

## Step 6 — Enter Evidence Information

The **Evidence Item Information** section was completed with the required forensic information.

The information includes:

* **Case Number**
* **Evidence Number**
* **Examiner Name**
* **Notes**

This information helps associate the forensic image with the corresponding investigation.

---

## Step 7 — Select Image Destination

The destination folder for storing the forensic image was specified.

An appropriate filename was also assigned to the forensic image.

The image fragment size was configured according to the acquisition requirements.

FTK Imager allows the image to be stored as a single file or divided into multiple fragments.

---

## Step 8 — Enable Image Verification

The option:

**Verify images after they are created**

was enabled.

This allows FTK Imager to verify the integrity of the created forensic image after acquisition.

---

## Step 9 — Start the Acquisition

The **Start** option was selected to begin the disk imaging process.

FTK Imager created a forensic image of the selected storage device.

The original storage device remained the source evidence, while the acquired image was stored at the specified destination.

---

## Step 10 — Verify the Forensic Image

After the image creation process was completed, the **Image Summary** was examined.

FTK Imager calculated cryptographic hash values for the acquired image.

The verification process uses:

* **MD5**
* **SHA-1**

The calculated hash values were compared to verify the integrity of the acquired forensic image.

---

# 🔐 Hash Verification

Cryptographic hashing is used to verify whether the acquired forensic image maintains data integrity.

In this experiment, FTK Imager performs MD5 and SHA-1 checksum verification after image creation.

The basic verification process is:

```text
Target Storage Device
        ↓
FTK Imager
        ↓
Forensic Disk Image
        ↓
Hash Calculation
        ↓
MD5 / SHA-1 Verification
        ↓
Image Integrity Confirmed
```

Matching hash values indicate that the verification process completed successfully.

---

# 🔎 Observations

1. FTK Imager successfully provided the functionality required to create a forensic disk image.
2. The target USB storage device was selected as the source evidence.
3. Evidence information such as case number, evidence number, examiner name, and notes could be recorded during image creation.
4. The forensic image destination and filename were configured before acquisition.
5. FTK Imager provided multiple forensic image formats for acquisition.
6. Image verification was enabled after the image creation process.
7. MD5 and SHA-1 checksums were used for verifying the integrity of the created forensic image.

---

# 🧠 Findings

* FTK Imager can be used to create a forensic image of a storage device.
* Recording evidence information during acquisition helps maintain proper forensic documentation.
* Cryptographic hash verification provides a method for checking the integrity of the acquired image.
* The created forensic image can be used as a working copy for subsequent forensic examination while preserving the original evidence.

---

# 📊 Result

✅ **Experiment Successfully Completed**

The target USB storage device was successfully acquired using **AccessData FTK Imager**.

A forensic disk image was created and the image verification process was performed using **MD5 and SHA-1** cryptographic hashes.

---

# 📝 Conclusion

The experiment demonstrated the process of acquiring digital evidence from a storage device using **AccessData FTK Imager**.

The target storage device was selected, the forensic image parameters and evidence information were configured, and the image was created at the specified destination.

The acquired image was subsequently verified using **MD5 and SHA-1** hash values to ensure the integrity of the forensic acquisition.

