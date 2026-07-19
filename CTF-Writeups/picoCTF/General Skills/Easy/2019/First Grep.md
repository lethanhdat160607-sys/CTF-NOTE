# 🚩 First Grep - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `First Grep`
- **Key Skills And Tools:** convert from decimal to base
---

## 🔍 Challenge 

Can you find the flag in the file? This would be really tedious to look through manually, something tells me there is a better way.

The flag is in this file
.

### 🧪 Logic Extraction:

I used the `cat` command to read the file and the `grep` command (with hyphens) as output to search for the keyword picoCTF.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ cat file | grep picoCTF

```

## Run

. flag picoCTF{grep_is_good_to_find_things_e3C4b360}
