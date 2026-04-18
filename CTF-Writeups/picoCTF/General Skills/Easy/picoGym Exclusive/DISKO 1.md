# 🚩DISKO 1 - picoGym Exclusive

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `disko-1.dd`
- **Key Skills And Tools:** strings, 
---

## 🔍 Challenge 
Can you find the flag in this disk image?
Download the disk image here.

### 🧪 Logic Extraction:
ComponentDescriptionstringsA powerful utility that extracts all printable character sequences from a binary file. It ignores machine code and focuses on human-readable text.disko-1.ddA disk image file. The .dd extension represents a bit-for-bit (raw) copy of a storage drive or partition, commonly used in digital forensics.**`` (Pipe)**grep picoCTFA search tool used to filter the extracted text, showing only the lines that contain the "picoCTF" flag format.

<div align="center">
  <img width="718" height="73" alt="image" src="https://github.com/user-attachments/assets/cbc79c72-55a4-49c9-aeff-1318d6b3a1bb" />

</div>


## Run 
.flag picoCTF{1t5_ju5t_4_5tr1n9_e3408eef}
