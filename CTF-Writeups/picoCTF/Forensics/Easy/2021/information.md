# 🚩 information - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `pcap file`
- **Key Skills And Tools:** Aircrack-ng, Wireshark ,Password cracking and decryption
---

## 🔍 Challenge 

Files can always be changed in a secret way. Can you find the flag?
cat.jpg

### 🧪 Logic Extraction:
After downloading the image, I opened it but didn't see the flag. So I used the command `exiftool cat.jpg` to open the image and noticed two things: `Current IPTC Digest` and `License`. Because they were long and contained many characters, I encoded them into a flag. Based on my analysis of the codes for `Current IPTC Digest` and `License`, the `Current IPTC Digest` code consists of 32 characters, including numbers and letters from a to f. This is characteristic of `MD5`, which only allows 32 characters, making it quite restrictive. Therefore, I leaned towards `License` and analyzed the code, concluding it was `base64`. Why? I guessed it was `base64` because it showed `a-z`, `A-Z`, `0-9`, `+`, and `-`. Usually, it would show the characters I listed. If you see a long string with no spaces and no unusual special characters (like !, @, #, $, %, ^, *), it's highly likely to be base64. Another characteristic is that if there's an `=` or `==` symbol, it's 99% likely to be base64 code.


<div align="center">
  <img width="731" height="498" alt="image" src="https://github.com/user-attachments/assets/a78b5f4a-6a79-4107-8374-a90412c40a70" />


</div>


## Run 
.flag picoCTF{}
