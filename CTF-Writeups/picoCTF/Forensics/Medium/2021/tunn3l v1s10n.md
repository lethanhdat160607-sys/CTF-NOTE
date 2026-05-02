# 🚩tunn3l v1s10n - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `tunn3l_v1s10n`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

We found this file. Recover the flag.
tunn3l_v1s10n

### 🧪 Logic Extraction:


<div align="center">  
  <img width="574" height="332" alt="image" src="https://github.com/user-attachments/assets/739b2feb-a633-4ea7-9af8-80fc6258e1cc" />
</div>div>

<div align="center">
  <img width="1317" height="488" alt="image" src="https://github.com/user-attachments/assets/a638b5c8-3d82-46cf-9635-685ce272510b" />

</div>

```
┌──(kali㉿kali)-[~/Tools/CTF]
└─$ xxd tunn3l_v1s10n | head -n2 
00000000: 424d 8e26 2c00 0000 0000 36d0 0000 2800  BM.&,.....6...(.
00000010: 0000 6e04 0000 5203 0000 0100 1800 0000  ..n...R.........
```

```
┌──(kali㉿kali)-[~/Tools/CTF]
└─$ feh tunn3l_v1s10n      
                       
```
<div align="center"> 
  <img width="1234" height="587" alt="image" src="https://github.com/user-attachments/assets/1b60886b-d92d-42f3-b1c0-80e06c037415" />

</div>

## Run 
.flag picoCTF{s0_m3ta_9a8b5aa1}
