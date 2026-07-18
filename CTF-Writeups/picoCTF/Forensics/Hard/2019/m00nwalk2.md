# 🚩m00nwalk2 - picoCTF 2019

- **Category:** Forensics ⚙️
- **Difficulty:** Hard
- **Target File:** 
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

Revisit the last transmission. We think this transmission
 contains a hidden message. There are also some clues clue 1
, clue 2
, clue 3
.

### 🧪 Logic Extraction:

I used the `strings` command and got the flag immediately.
```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ strings memdump.mem | grep 'picoCTF{'          
picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}

```

## Run 
.flag picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}

