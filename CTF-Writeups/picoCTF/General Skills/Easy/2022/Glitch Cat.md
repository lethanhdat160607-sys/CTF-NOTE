# 🚩 Glitch Cat.md - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `nc saturn.picoctf.net 51246`
- **Key Skills And Tools:** python, connect to server
---

## 🔍 Challenge 

Our flag printing service has started glitching!

`nc saturn.picoctf.net 51246`.


### 🧪 Logic Extraction:

I connected to the challenge server and saw a piece of code that indicated Python was needed to run it. I ran the `print` python command to get the flag result.
```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$  nc saturn.picoctf.net 51246
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ python3          
Python 3.13.12 (main, Feb  4 2026, 15:06:39) [GCC 15.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print('picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
... )
picoCTF{gl17ch_m3_n07_bda68f75}

```

## Run

. flag picoCTF{gl17ch_m3_n07_bda68f75}


