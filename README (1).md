# VOID CTF 2026: Write-Up

**Name:** Aryan Bhardwaj | **Branch:** CSE-AIML | **Roll No:** 202401100400053 | **Team:** ALPHA

**Challenges solved:** 13 (Welcome to the Void, Afterimage, Afterlife, The Vault, 3000 Files Later, CIPHERFALL, The last broadcast, Do Not Search, Left Behind, Fractured Truth, Aegis, Redacted, bing chilling)

---

## 1. Welcome to the Void

**Category:** Sanity | **Points:** 100

**Approach Taken:**

- Opened the challenge page and read the welcome message and the CTF rules.
- Since it was a sanity challenge, the flag was given in the instructions themselves, so I copied it exactly in the VOID{...} format.
- Submitted it on the platform to confirm that my account and team were working.

---

## 2. Afterimage

**Category:** Steganography | **Points:** 300

**Approach Taken:**

- Opened the given image and saw nothing unusual, so I checked its file type and metadata first.
- The name suggested something was left behind after the image, so I checked for data hidden in the pixel colour channels and for extra bytes after the end of the file.
- Extracted the hidden data and read the flag from it.

---

## 3. Afterlife

**Category:** PWN | **Points:** 250

**Approach Taken:**

- Checked the provided binary's file type and protections (NX, canary, PIE) before running it.
- Ran the program with a very long input, which crashed it and showed that the input is copied into a buffer without a proper length check.
- Found the exact offset to the return address using a cyclic pattern and wrote an exploit script with pwntools to redirect the execution.
- Tested the exploit locally, then ran it against the remote service to read the flag.

---

## 4. The Vault

**Category:** Steganography | **Points:** 150

**Approach Taken:**

- The description spoke about a locked vault, so I guessed that the file was hiding another file behind a password.
- Ran strings and a file-carving tool on it to look for embedded data and for a hint about the password.
- Used the hint to open the vault, extracted the hidden file and found the flag inside it.

---

## 5. 3000 Files Later

**Category:** Forensics | **Points:** 500

**Approach Taken:**

- Extracted the archive and found about 3000 files, which was far too many to open one by one.
- Wrote a short script to search every file for the VOID{ pattern and to compare file sizes, timestamps and hashes, so that the files differing from the rest stood out.
- Analysed those odd files in detail and put the recovered content together to get the flag.

---

## 6. CIPHERFALL

**Category:** Cryptography | **Points:** 400

**Approach Taken:**

- Read the description and studied the given ciphertext, looking at its length, character set and repeating patterns.
- The name suggested the message was encrypted in layers, so I identified the outermost layer, removed it and repeated the same process for each next layer.
- Wrote a Python script that reverses every layer in the correct order and recovered the plaintext flag.

---

## 7. The last broadcast

**Category:** OSINT | **Points:** 300

**Approach Taken:**

- Read the description carefully and noted down every clue such as names, places and dates.
- Searched these clues online and followed them through public posts and web archives until I reached the final broadcast.
- Checked that every detail matched the question and wrote the answer in the flag format.

---

## 8. Do Not Search

**Category:** OSINT | **Points:** 200

**Approach Taken:**

- The title warned against searching directly, so I did not paste the question into a search engine and studied the given clue itself first.
- Picked out the small details in it, such as a username or unusual words, and used them to look at specific public sources.
- Found the exact information the question asked for and formed the flag from it.

---

## 9. Left Behind

**Category:** Forensics | **Points:** 200

**Approach Taken:**

- Opened the given PCAPNG capture and analysed it with a Python script to examine the USB communication and look for unusual device activity.
- Grouped the captured records by device and endpoint, which separated the normal mouse traffic from the suspicious keyboard input.
- Decoded the HID keyboard reports by converting the keycodes and modifier states (such as Shift) into characters to reconstruct the injected keystrokes.
- Accounted for the keyboard editing behaviour, such as characters being deleted and retyped, to remove the decoy text and recover the actual flag.

---

## 10. Fractured Truth

**Category:** Steganography | **Points:** 300

**Approach Taken:**

- Looked at the provided files and noticed that the information was broken into pieces instead of being in one place.
- Extracted each fragment separately from where it was hidden, such as the image data, metadata or extra bytes at the end of a file.
- Arranged the pieces in the correct order and joined them to get the full flag.

---

## 11. Aegis

**Category:** Reverse Engineering | **Points:** 350

**Approach Taken:**

- Identified the file type, ran the program to see how it behaves and then opened it in a decompiler.
- The name hinted at a protection, so I followed the code from main to the routine that validates the input and studied how it guards the flag.
- Reversed that check on paper and in a small script to find the correct input, then ran the program with it to get the flag.

---

## 12. Redacted

**Category:** Web Exploitation | **Points:** 200

**Approach Taken:**

- Opened the website and saw that the important part of the page was blacked out.
- Used view-source and the browser dev tools and found that the content was only hidden on screen and was still present in the page or in a request.
- Read the hidden content directly from there and obtained the flag.

---

## 13. bing chilling

**Category:** Reverse Engineering | **Points:** 200

**Approach Taken:**

- Checked what kind of file it was and ran it once to see its behaviour.
- Opened it in a decompiler and read the main function along with the strings and constants it uses.
- Understood how the program produces the flag, reproduced that logic and got the flag.

---

