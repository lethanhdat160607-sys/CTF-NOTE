# 🚩Matryoshka doll.md - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `dolls.jpg`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?
Image: dolls.jpg

### 🧪 Logic Extraction:


```
┌──(kali㉿kali)-[~/Tools/CTF]
└─$ binwalk -e dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378933, uncompressed size: 383920, name: base_images/2_c.jpg

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/CTF]
└─$ ls
dolls.jpg  _dolls.jpg.extracted

```


```

```
## Run 
.flag picoCTF{s0_m3ta_9a8b5aa1}
