
# 🧪 EXPERIMENT 04 — Analyze Email Headers and Detect Email Spoofing Using MHA

---

## 🎯 Objective

To extract, analyze, and interpret email headers to trace the origin of an email, verify email authentication mechanisms such as **SPF, DKIM, and DMARC**, and identify whether an email may be spoofed or associated with a phishing attempt using Mail Header Analyzer (MHA) tools.

---

## 🧰 Tools / Requirements

* **Operating System:** Windows, Linux, or macOS
* **Email Client:** Web browser with Gmail, Outlook, or Yahoo
* **Mail Header Analysis Tool:** MXToolbox Mail Header Analyzer
* **IP Analysis Tool:** WHOIS IP Lookup

---

## 📋 Experiment Scenario

Every email transmitted over the Internet contains an **email header** containing metadata about the message.

Email headers contain information about the message's delivery path, sending infrastructure, routing servers, and authentication results.

Analyzing these details can help investigators examine the origin and authenticity of an email and identify indicators of spoofing or suspicious activity.

The experiment focused on analyzing:

* Email routing information
* Sending IP address
* SPF authentication
* DKIM authentication
* DMARC authentication
* WHOIS information
* Message-ID
* Return-Path
* Received headers
* Email delivery timing

---

# 🔐 Email Authentication Protocols

## SPF — Sender Policy Framework

**SPF** is an email authentication mechanism that checks whether the sending IP address is authorized to send email on behalf of the claimed domain.

It helps identify whether the sending server is permitted by the domain's SPF policy.

---

## DKIM — DomainKeys Identified Mail

**DKIM** uses a cryptographic signature associated with the sending domain.

It helps verify that the email content has not been modified during transmission and that the message is associated with the signing domain.

---

## DMARC — Domain-based Message Authentication, Reporting, and Conformance

**DMARC** uses SPF and DKIM authentication information to help validate email messages.

It also allows a domain to specify how receiving systems should handle messages that fail authentication.

---

# ⚙️ Procedure

## Step 1 — Access the Email

The target email was located in the email account.

The email could be located in either the Inbox or Spam folder depending on how the email service classified it.

The email was opened to examine the sender information and subject.

---

## Step 2 — Extract the Raw Email Header

The original email header was opened to obtain the hidden metadata associated with the message.

For Gmail, the **Show original** option can be accessed from the email's More menu.

For Outlook, the email headers can be accessed through the message properties.

For Yahoo, the raw message can be viewed using the corresponding raw-message option.

The complete raw header information was copied for further analysis.

The header contains information such as:

* `Received` fields
* `Message-ID`
* Authentication results
* Routing information
* Sender-related information

---

## Step 3 — Analyze the Header Using MXToolbox

The extracted raw email header was entered into the **MXToolbox Mail Header Analyzer**.

The header was submitted for analysis.

The analyzer was used to examine the email's delivery and relay information.

The chronological **hops** through which the email traveled were examined.

The analysis focused on:

* Sending server
* Receiving server
* Intermediate mail servers
* Delivery sequence
* Routing path
* Delays between server handoffs

---

## Step 4 — Examine SPF, DKIM, and DMARC

The authentication results provided by the header analyzer were examined.

The SPF result was checked to determine whether the sending IP address was authorized by the sender's domain.

The DKIM result was examined to verify the cryptographic authentication associated with the email.

The DMARC result was examined to determine whether the email satisfied the domain's authentication policy.

The sending IP address identified during the analysis was:

```text id="q3m7vx"
103.52.180.165
```

The SPF, DKIM, and DMARC results were reviewed together to assess the authenticity of the email.

---

## Step 5 — Verify the Sending IP Address

The primary sending IP address was extracted from the `Received` header information.

The identified IP address was:

```text id="p8k4zn"
103.52.180.165
```

A WHOIS lookup was then performed on the IP address.

The purpose of the WHOIS analysis was to identify:

* Registered organization
* IP ownership information
* Geographical information
* Hosting or network organization

The identified organization was **Netcore-In**.

---

# 🔎 Forensic Findings & Analysis

## 1. Sender Domain

The analyzed sender domain was:

```text id="j5v2rb"
communication.vodafoneidea.in
```

---

## 2. Sending IP Address

The primary sending IP address identified from the email header was:

```text id="c7n9mw"
103.52.180.165
```

---

## 3. Authentication Status

The analyzed email **passed the primary SPF, DKIM, and DMARC authentication checks**.

The sending IP address was identified as authorized to send on behalf of the sender domain.

---

## 4. WHOIS Verification

The WHOIS analysis associated the sending IP address with **Netcore-In**.

The experiment identifies Netcore-In as a bulk SMS and email gateway service used by telecom providers.

---

## 5. Hop-by-Hop Routing Analysis

The chronological `Received` fields were examined to understand the route followed by the email.

The analysis indicated a logical network path from the originating server through the mail infrastructure to Google's mail transfer servers.

No forged intermediate hops were identified during the analysis.

---

## 6. Timestamp and Latency Verification

The timestamps contained in the email headers were examined at each server handoff.

The observed timestamps indicated normal transit times without suspicious delays or rerouting.

---

## 7. Message-ID Analysis

The **Message-ID** was examined as part of the header analysis.

The Message-ID followed the expected format associated with an enterprise mail server.

---

## 8. Return-Path Analysis

The **Return-Path** information was examined and found to align with the sender's mail infrastructure.

This was consistent with the infrastructure identified during the header analysis.

---

## 9. X-Headers and Spam Assessment

Custom **X-Headers** were examined as part of the analysis.

The email had triggered spam filtering based on promotional-content heuristics.

The analysis indicated that this classification was not caused by a failure of the primary email authentication protocols.

---

# 🧠 Findings

* Email headers provide important metadata for investigating the origin and delivery path of an email.
* The `Received` fields can be examined to reconstruct the chronological routing path.
* SPF can be used to determine whether a sending IP is authorized by a domain.
* DKIM provides cryptographic verification associated with the sending domain.
* DMARC combines authentication information and domain policy to help evaluate email authenticity.
* WHOIS information can provide information about the organization associated with an IP address.
* Message-ID and Return-Path information can provide additional indicators about the sending infrastructure.
* In this analysis, the email passed SPF, DKIM, and DMARC checks.
* The analyzed routing information and authentication results did not indicate email spoofing in the examined message.

---

# 🛡️ Spoofing Analysis

Based on the header analysis described in the experiment:

* **SPF:** Passed
* **DKIM:** Passed
* **DMARC:** Passed
* **Sending IP:** `103.52.180.165`
* **Sender Domain:** `communication.vodafoneidea.in`
* **WHOIS Organization:** Netcore-In
* **Routing Analysis:** No forged intermediate hops identified
* **Return-Path:** Aligned with the sender infrastructure

Although the email had been classified as spam by Gmail, the analysis attributed this classification to promotional-content filtering rather than a failure of the primary authentication mechanisms.

The experiment therefore concluded that the analyzed email was **not spoofed**.

---

# 📊 Result

✅ **Experiment Successfully Completed**

The email header was successfully extracted and analyzed using **MXToolbox Mail Header Analyzer**.

The email's routing information, sending IP address, SPF, DKIM, and DMARC authentication results were examined.

The sending IP address was additionally verified using WHOIS information.

The analysis demonstrated how email headers can be used to trace email delivery paths and investigate potential email spoofing.

---

# 📝 Conclusion

The experiment demonstrated the forensic analysis of email headers using **Mail Header Analyzer (MHA)** tools.

The raw email header was extracted and examined to identify the sender domain, sending IP address, routing path, authentication results, and other relevant metadata.

SPF, DKIM, and DMARC results were analyzed along with WHOIS information for the sending IP address.

Based on the documented analysis, the examined email passed the primary authentication checks and was determined not to be spoofed.
