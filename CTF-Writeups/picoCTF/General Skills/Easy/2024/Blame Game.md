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
I used the list command to check the directory and files for anything unusual, and I found a `.git` file.

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

```         
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git reflog

```

<div align="center">
  <img width="1126" height="487" alt="image" src="https://github.com/user-attachments/assets/4a5c9bb3-72f8-44ef-abe9-6142fc7e2b91" />

</div>


```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git checkout 2466feb
Previous HEAD position was 05f26d1 create top secret project
HEAD is now at 2466feb optimize file size of prod code
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ cat message.py      
print("Hello, World!"
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log             
commit 2466febd40004b9ca644ce924181d07e23dcfaeb (HEAD)
Author: picoCTF{@sk_th3_1nt3rn_cfca95b2} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:06 2024 +0000

    optimize file size of prod code

commit 05f26d123cde97b714aaae28ba8f18db3f385af5
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:06 2024 +0000

    create top secret project
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log
commit 2466febd40004b9ca644ce924181d07e23dcfaeb (HEAD)
Author: picoCTF{@sk_th3_1nt3rn_cfca95b2} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:06 2024 +0000

    optimize file size of prod code

commit 05f26d123cde97b714aaae28ba8f18db3f385af5
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:06 2024 +0000

    create top secret project

```
## Run

. flag picoCTF{@sk_th3_1nt3rn_cfca95b2}

