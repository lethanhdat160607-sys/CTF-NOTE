# 🚩 runme.py - picoCTF 2022

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `runme.py`
- **Key Skills And Tools:** python, reading file data
---

## 🔍 Challenge 

Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 in the same directory too.

### 🧪 Logic Extraction:

I used the `cat` command to extract the data, and inside it there's a flag.
```
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat runme.py
#!/usr/bin/python3
################################################################################
# Python script which just prints the flag
################################################################################

flag ='picoCTF{run_s4n1ty_run}'
print(flag)


```



## Run

. flag picoCTF{run_s4n1ty_run}


