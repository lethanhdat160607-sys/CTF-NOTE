# 🚩 Time Machine - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `challenge.zip`
- **Key Skills And Tools:** git, cat, reading data file
---

## 🔍 Challenge 

What was I last working on? I remember writing a note to help me remember...

You can download the challenge files here:

challenge.zip


### 🧪 Logic Extraction:

I used the `unzip` command to extract the files, `cd` to enter the `drop-in` directory, and `git log` to view the history, which revealed the flag.
```
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ unzip challenge.zip

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ ls
challenge.zip  drop-in
                                                                                                                                                        
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cd drop-in
                                                                                                                                                        
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log         
commit 89d296ef533525a1378529be66b22d6a2c01e530 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:22 2024 +0000

    picoCTF{t1m3m@ch1n3_186cd7d7}

```

## Run

. flag picoCTF{t1m3m@ch1n3_186cd7d7}

