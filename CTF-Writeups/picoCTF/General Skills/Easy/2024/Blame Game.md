# 🚩 Blame Game - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `challenge.zip`
- **Key Skills And Tools:** git, cat, , reading data file
---

## 🔍 Challenge 

Someone's commits seems to be preventing the program from working. Who is it?

You can download the challenge files here:

challenge.zip

### 🧪 Logic Extraction:

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ ls
challenge.zip  drop-in
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cd drop-in
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ ls
message.py
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ ls -la
total 16
drwxr-xr-x 3 kali kali 4096 Mar 11  2024 .
drwxrwxr-x 3 kali kali 4096 Aug  6 03:21 ..
drwxr-xr-x 8 kali kali 4096 Mar 11  2024 .git
-rw-r--r-- 1 kali kali   22 Mar 11  2024 message.py
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ cat message.py
print("Hello, World!"
                      
```


## Run

. flag picoCTF{@sk_th3_1nt3rn_cfca95b2}

