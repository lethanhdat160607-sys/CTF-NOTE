# 🚩CanYouSee - picoCTF 2024

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `ukn_reality.jpg`
- **Key Skills And Tools:** Aircrack-ng, Wireshark ,Password cracking and decryption
---

## 🔍 Challenge 
How about some hide and seek?
Download this file here.

### 🧪 Logic Extraction:
I used the command `exiftool ukn_reality.jpg` to view the hidden data in the image and immediately noticed the Attribution URL because I saw that it had base64 encoding.Why? I guessed it was base64 because it displays a-z, A-Z, 0-9, +, and -. Typically, it will display the characters I've listed. If you see a long string with no spaces and no unusual special characters (like !, @, #, $, %, ^, *), it's most likely base64 code. Another characteristic is that if there's an = or == symbol, there's a 99% chance it's base64 code.

<div align="center">
    <img width="731" height="498" alt="image" src="https://github.com/user-attachments/assets/c9272a43-b2f9-47c0-a59d-b66768ab6d0b" />

</div>

#
I used Cyberchef to encode the `base64` code and get the flag.
<div align="center">
    <img width="785" height="234" alt="image" src="https://github.com/user-attachments/assets/509e0824-0b09-46b0-bfb4-578931ae8660" />
    <p>Cyberchef base64 </p>
</div>

## Run 
.flag picoCTF{ME74D47A_HIDD3N_6a9f5ac4}

