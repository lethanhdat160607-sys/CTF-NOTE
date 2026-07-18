# 🚩Timeline  - picoCTF 2026

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `partition4.img.gz`
- **Key Skills And Tools:** strings, reading data
---

## 🔍 Challenge 

Can you find the flag in this disk image? Wrap what you find in the picoCTF flag format.

Download the disk image here.

### 🧪 Logic Extraction:

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ fls -r -m / partition4.img > body.txt
 ```

```                                                                                                                                                          
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt > timeline.txt
Old package separator "'" deprecated at /usr/bin/mactime line 154.
Old package separator "'" deprecated at /usr/bin/mactime line 167.
                                                                                                                                                           
```

```
                                                                                                                                                                                  
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt  
```

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt | grep macb

```

<div align="center">
  <img width="1363" height="536" alt="image" src="https://github.com/user-attachments/assets/39799a59-3fb6-4a4f-bb24-12786d1ff8a0" />

</div>  

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 9   

                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 4943

poweroff
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 33020

shutdown                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 32716

NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 32716 | base64 -d

573417h13r_7h4n_7h3_1457_58527bb222

```

## Run 
.flag picoCTF{573417h13r_7h4n_7h3_1457_58527bb222}




