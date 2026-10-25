<h1 align="center">🏴‍☠️ VOID CTF 2026 — Write-Up</h1>

<p align="center">
  <img src="https://img.shields.io/badge/CTF-VOID%20CTF%202026-0E7C86?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Team-ALPHA-14213D?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Solved-13-brightgreen?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Points-3450-orange?style=for-the-badge" />
</p>

<p align="center"><i>Individual write-up of every challenge I solved during VOID CTF 2026.</i></p>

---

## 👤 Participant

| | |
|---|---|
| **Name** | Aryan Bhardwaj |
| **Branch** | CSE-AIML |
| **Roll No** | 202401100400053 |
| **Team** | ALPHA |
| **Challenges Solved** | 13 |
| **Total Points** | 3450 |

## 📊 Solve Summary

| # | Challenge | Category | Points |
|:-:|-----------|----------|:------:|
| 1 | [Welcome to the Void](#1-welcome-to-the-void) | 🧘 Sanity | 100 |
| 2 | [Afterimage](#2-afterimage) | 🖼️ Steganography | 300 |
| 3 | [Afterlife](#3-afterlife) | 💥 PWN | 250 |
| 4 | [The Vault](#4-the-vault) | 🖼️ Steganography | 150 |
| 5 | [3000 Files Later](#5-3000-files-later) | 🕵️ Forensics | 500 |
| 6 | [CIPHERFALL](#6-cipherfall) | 🔐 Cryptography | 400 |
| 7 | [The last broadcast](#7-the-last-broadcast) | 🌐 OSINT | 300 |
| 8 | [Do Not Search](#8-do-not-search) | 🌐 OSINT | 200 |
| 9 | [Left Behind](#9-left-behind) | 🕵️ Forensics | 200 |
| 10 | [Fractured Truth](#10-fractured-truth) | 🖼️ Steganography | 300 |
| 11 | [Aegis](#11-aegis) | ⚙️ Reverse Engineering | 350 |
| 12 | [Redacted](#12-redacted) | 🕸️ Web Exploitation | 200 |
| 13 | [bing chilling](#13-bing-chilling) | ⚙️ Reverse Engineering | 200 |
| | **Total** | | **3450** |

## 🗂️ Category Breakdown

- 🧘 **Sanity** — 1 challenge
- 🖼️ **Steganography** — 3 challenges
- 💥 **PWN** — 1 challenge
- 🕵️ **Forensics** — 2 challenges
- 🔐 **Cryptography** — 1 challenge
- 🌐 **OSINT** — 2 challenges
- ⚙️ **Reverse Engineering** — 2 challenges
- 🕸️ **Web Exploitation** — 1 challenge

---

## 🚩 Challenge Write-Ups

### 1. Welcome to the Void

> 🧘 **Category:** Sanity &nbsp;|&nbsp; ⭐ **Points:** 100

**Approach Taken:**

1. Opened the challenge page and read the welcome message and the CTF rules.
2. Since it was a sanity challenge, the flag was given in the instructions themselves, so I copied it exactly in the VOID{...} format.
3. Submitted it on the platform to confirm that my account and team were working.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 2. Afterimage

> 🖼️ **Category:** Steganography &nbsp;|&nbsp; ⭐ **Points:** 300

**Approach Taken:**

1. Opened the given image and saw nothing unusual, so I checked its file type and metadata first.
2. The name suggested something was left behind after the image, so I checked for data hidden in the pixel colour channels and for extra bytes after the end of the file.
3. Extracted the hidden data and read the flag from it.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 3. Afterlife

> 💥 **Category:** PWN &nbsp;|&nbsp; ⭐ **Points:** 250

**Approach Taken:**

1. Checked the provided binary's file type and protections (NX, canary, PIE) before running it.
2. Ran the program with a very long input, which crashed it and showed that the input is copied into a buffer without a proper length check.
3. Found the exact offset to the return address using a cyclic pattern and wrote an exploit script with pwntools to redirect the execution.
4. Tested the exploit locally, then ran it against the remote service to read the flag.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 4. The Vault

> 🖼️ **Category:** Steganography &nbsp;|&nbsp; ⭐ **Points:** 150

**Approach Taken:**

1. The description spoke about a locked vault, so I guessed that the file was hiding another file behind a password.
2. Ran strings and a file-carving tool on it to look for embedded data and for a hint about the password.
3. Used the hint to open the vault, extracted the hidden file and found the flag inside it.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 5. 3000 Files Later

> 🕵️ **Category:** Forensics &nbsp;|&nbsp; ⭐ **Points:** 500

**Approach Taken:**

1. Extracted the archive and found about 3000 files, which was far too many to open one by one.
2. Wrote a short script to search every file for the VOID{ pattern and to compare file sizes, timestamps and hashes, so that the files differing from the rest stood out.
3. Analysed those odd files in detail and put the recovered content together to get the flag.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 6. CIPHERFALL

> 🔐 **Category:** Cryptography &nbsp;|&nbsp; ⭐ **Points:** 400

**Approach Taken:**

1. Read the description and studied the given ciphertext, looking at its length, character set and repeating patterns.
2. The name suggested the message was encrypted in layers, so I identified the outermost layer, removed it and repeated the same process for each next layer.
3. Wrote a Python script that reverses every layer in the correct order and recovered the plaintext flag.

<p align="right"><a href="#-solve-summary">⬆ back to summary</a></p>

---

### 7. The last broadcast

> 🌐 **Category:** OSINT &nbsp;|&nbsp; ⭐ **Points:** 300

**Approach Taken:**

1. Read the description carefully and noted down every clue such as names, places and dates.
2. Searched these clues online and followed them through public posts and web archives until I reached the final broadcast.
3. Checked that every detail matched the question and wrote the answer in the flag format.

<p align="right"><a href="#-solve-summary">⬆ back to
