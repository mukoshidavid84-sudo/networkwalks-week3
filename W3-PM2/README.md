# Network Walks Cybersecurity Internship 2026 — Week 3 (W3-PM2)
**Topic:** Client-Side PDF Hash Extraction & Browser-Based Password Auditing  
**Author:** David Mukoshi  

## Overview
This lab demonstrates browser-based cryptographic hash extraction and offline wordlist auditing against password-protected PDF documents using the **Networkwalks Hash Calculator** and **Networkwalks Password Cracker**.

---

## Lab Workflow & Execution Log

### 1. Target 1 (`My-Locked-PDF1.pdf`) — Hash Extraction, Cracking & Flag 1
- Parsed `My-Locked-PDF1.pdf` (`65.2 KB`, `Version: V4`, `Revision: R4`, `Key length: 128 bit`) locally in the **Networkwalks Hash Calculator** (`PDF` tab) to generate its `$pdf$4*4*128*` hash string without transmitting file contents externally.
- Loaded the extracted hash into the **Networkwalks Password Cracker**, matching plaintext password **`password1`** at attempt `91 / 100` (`9 pw/s`), and unlocked the PDF to retrieve **Flag 1**.

![PDF 1 Hash Extraction in Networkwalks Hash Calculator](image2.png)
![PDF 1 Password Cracked](image1.png)
![PDF 1 Flag Captured](image3.jpg)

### 2. Target 2 (`PDF 2`) — Flag 2 Captured
- Extracted the `$pdf$4*4*128*` hash for `PDF 2` using the Networkwalks Hash Calculator, recovered the plaintext password (`good-luck`) via the Networkwalks Password Cracker, and unlocked the document to retrieve **Flag 2**.

![PDF 2 Flag Captured](image4.jpg)

### 3. Target 3 (`PDF 3`) — Password Cracked & Flag 3 Captured
- Extracted the `$pdf$4*4*128*` hash for `PDF 3` locally, matched the keyboard-walk password **`1qaz2wsx`** in the Networkwalks Password Cracker, and unlocked the document to retrieve **Flag 3**.

![PDF 3 Password Cracked](image5.png)
![PDF 3 Flag Captured](image6.png)

---

## Results & Captured Flags Summary

| Target Document | Encryption Specs | Recovered Password | Captured Flag |
| :--- | :--- | :--- | :--- |
| `My-Locked-PDF1.pdf` | `V4 / R4 (128-bit)` | `password1` | `nw{networkwalks_flag1_jtr_270521_1}` |
| `PDF 2` | `V4 / R4 (128-bit)` | `good-luck` | `nw{networkwalks_persistence_jtr_270521}` |
| `PDF 3` | `V4 / R4 (128-bit)` | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` |

---

## Key Security Takeaways & Remediation
- **Client-Side Privacy Advantage:** Performing hash extraction locally in the browser prevents sensitive corporate documents from being uploaded to third-party servers during an audit.
- **Password Entropy:** Even with 128-bit encryption, weak dictionary credentials (`password1`) and predictable keyboard walks (`1qaz2wsx`) are recovered within seconds. Organizations should enforce 14+ character passphrases and AES-256 PDF encryption.
