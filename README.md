# Network Walks Cybersecurity Internship 2026 — Week 3 (W3-PM1)
**Topic:** Offline Password Cracking & Hash Extraction with John the Ripper & Johnny GUI  
**Author:** David Mukoshi  

## Overview
This lab demonstrates practical cryptographic hash extraction and offline dictionary/rule-based password recovery against password-protected PDF documents using **John the Ripper (`1.9.0-jumbo-1`)** integrated with **Johnny GUI** on Windows.

---

## Lab Workflow & Execution Log

### 1. Cryptographic Hash Extraction
- Extracted `$pdf$` hash strings from three encrypted target PDFs (`My Locked PDF1.pdf`, `PDF 2`, and `PDF 3`) using OnlineHashCrack's PDF Hash Extractor (`Standard Security Handler V4 / Revision 4, 128-bit`).

![OnlineHashCrack PDF Hash Extraction](image1.png)

### 2. Tool & Binary Configuration
- Deployed `john-1.9.0-jumbo-1-win64` alongside `johnny_2.2_win` on Windows 11.
- Configured the executable path (`C:/john/john-1.9.0-jumbo-1-win64/run/john.exe`) in **Johnny GUI → Settings** and verified OpenMP/AVX2 engine detection.

![Johnny GUI Binary Configuration](image2.png)

### 3. Target 1 (`My Locked PDF1.pdf`) — Cracked & Flag Captured
- Loaded the extracted hash into Johnny GUI (`[format=PDF]`) and recovered the plaintext password **`good-luck`**.
- Unlocked `My Locked PDF1.pdf` to retrieve **Flag 1**.

![PDF 1 Password Cracked in Johnny](image3.png)
![PDF 1 Flag Captured](image4.png)

### 4. Target 2 (`PDF 2`) — Cracked & Flag Captured
- Extracted and loaded the second PDF hash into Johnny GUI, recovering the plaintext password **`password1`**.
- Unlocked `PDF 2` to retrieve **Flag 2**.

![PDF 2 Password Cracked in Johnny](image5.png)
![PDF 2 Flag Captured](image6.png)

### 5. Target 3 (`PDF 3`) — Cracked & Flag Captured
- Extracted and loaded the third PDF hash into Johnny GUI, recovering the keyboard-walk password **`1qaz2wsx`**.
- Unlocked `PDF 3` to retrieve **Flag 3**.

![PDF 3 Password Cracked in Johnny](image7.png)
![PDF 3 Flag Captured](image8.png)

---

## Results & Captured Flags Summary

| Target Document | Encryption / Hash Format | Recovered Password | Captured Flag |
| :--- | :--- | :--- | :--- |
| `My Locked PDF1.pdf` | `$pdf$4*4*128*` (128-bit) | `good-luck` | `nw{cybersecurity_flag_captured_2608}` |
| `PDF 2` | `$pdf$4*4*128*` (128-bit) | `password1` | `nw{networkwalks_persistence_jtr_270521}` |
| `PDF 3` | `$pdf$4*4*128*` (128-bit) | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` |

---

## Key Security Takeaways & Remediation
- **Vulnerability:** All three recovered passwords (`good-luck`, `password1`, and the keyboard-walk pattern `1qaz2wsx`) fall immediately to standard dictionary and keyboard-pattern wordlists despite 128-bit PDF encryption.
- **Remediation:** Enforce high-entropy passphrases (14+ characters, avoiding keyboard walks and common dictionary terms) and upgrade document encryption to AES-256 (PDF 2.0 / Acrobat X+) to increase computational cracking resistance.
