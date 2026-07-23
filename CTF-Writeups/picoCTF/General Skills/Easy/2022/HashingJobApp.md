# 🚩 HashingJobApp - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `nc saturn.picoctf.net 55150`
- **Key Skills And Tools:** md5, connect to server
---

## 🔍 Challenge 

If you want to hash with the best, beat this test!

`nc saturn.picoctf.net 55150`.

### 🧪 Logic Extraction:

I used the online `MD5` tool, entered the answer, and got the flag.

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ nc saturn.picoctf.net 55150

Please md5 hash the text between quotes, excluding the quotes: 'Helen Keller'
Answer: 
c0aac1554fe46e67f218df124c318054
c0aac1554fe46e67f218df124c318054
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Chinatown'
Answer: 
09e49bb61f0323a3bfbe8937e2e031e8
09e49bb61f0323a3bfbe8937e2e031e8
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'King Arthur'
Answer: 
36304aebe9f3d880416be62d941d6fed
36304aebe9f3d880416be62d941d6fed
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}
```

## Run

. flag picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}


