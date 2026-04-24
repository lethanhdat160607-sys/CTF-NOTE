# 🚩extensions - picoCTF 2019

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `flag.txt`
- **Key Skills And Tools:** xxd, mv, exiftool, data extraction
---

## 🔍 Challenge 

This is a really weird text file. Can you find the flag?
Get the flag from TXT.

### 🧪 Logic Extraction:

This challenge involves using the `exiftool` command to probe for flags indicating that the file is a .png image file.

<div align="center">
  <img width="580" height="350" alt="image" src="https://github.com/user-attachments/assets/90cf4b7a-ae5a-4a8a-b5af-c67897ad167c" />

</div>

#
Next, I used the `xxd` command to check for any suspicious data and found nothing suspicious.
<div align="center">
  <img width="610" height="298" alt="image" src="https://github.com/user-attachments/assets/72add88c-e0a0-4962-9de2-769b3bf5f46c" />
</div>

I used the `mv` command to convert the file back to an image file, and when I opened it, you had the flag. It's that simple.

## Run 
.flag picoCTF{now_you_know_about_extensions}
