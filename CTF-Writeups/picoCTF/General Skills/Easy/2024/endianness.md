# 🚩 endianness - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `flag.c`
- **Key Skills And Tools:** git, cat, reading data file
---

## 🔍 Challenge 

Know of little and big endian?

Source

nc titan.picoctf.net 51618


### 🧪 Logic Extraction:

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ nc titan.picoctf.net 51618

Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: qyfbo
Enter the Little Endian representation: 6f62667971
Correct Little Endian representation!
Enter the Big Endian representation: 717966626f
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_cfe38ef0}

```

<div align="center">
  <img width="881" height="439" alt="image" src="https://github.com/user-attachments/assets/e97a2c1d-bd86-478f-86b5-e850270ef41b" />

</div>

## Run

. flag picoCTF{3ndi4n_sw4p_su33ess_cfe38ef0}
