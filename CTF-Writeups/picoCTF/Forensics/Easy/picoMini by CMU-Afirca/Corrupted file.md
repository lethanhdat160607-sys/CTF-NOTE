# 🚩Corrupted file - picoMini by CMU-Afirca 

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `file`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

This file seems broken... or is it? Maybe a couple of bytes could make all the difference. Can you figure out how to bring it back to life?
Download the file here.

### 🧪 Logic Extraction:


<div align="center">
  <img width="641" height="228" alt="image" src="https://github.com/user-attachments/assets/9d12cbb7-d966-4d07-804e-f02726ad7dd5" />
  <p> aaaaaaaaaaa</p>
  <img width="607" height="310" alt="image" src="https://github.com/user-attachments/assets/18d30add-06f8-405c-a252-8bd485cab7cb" />
  <p>aaaaaaaaaa </p>
</div>

#

```
┌──(kali㉿kali)-[~/Tools]
└─$ hexedit file 
         
┌──(kali㉿kali)-[~/Tools]
└─$ file file 
file: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 800x500, components 3

┌──(kali㉿kali)-[~/Tools]
└─$ mv file file.jpeg  
```

## Run 
.flag picoCTF{r3st0r1ng_th3_by73s_efd8c6c0}
