# 🚩 Collaborative Development - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `challenge.zip`
- **Key Skills And Tools:** zip, reading data file
---

## 🔍 Challenge 

My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?

You can download the challenge files here:

challenge.zip

### 🧪 Logic Extraction:

I used the `unzip` command to extract the archive
```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ unzip challenge.zip


┌──(kali㉿kali)-[~/Tools/Misc]
└─$ ls
challenge.zip  drop-in
```
- I used the `git init` command to reinitialize a Git repository in the current directory. This action resets the Git configuration without losing existing data files.
- I used the `git branch -a` command to list all existing branches in the repository; the output showed four branches (`feature/part-1`, `feature/part-2`, `feature/part-3`, and `main`), with the asterisk (*) indicating that I was currently on the `main` branch.

```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git init                                              
Reinitialized existing Git repository in /home/kali/Tools/Misc/drop-in/.git/
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git branch -a 
  feature/part-1
  feature/part-2
  feature/part-3
* main
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ cat flag.py  
print("Printing the flag...")

```

```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log '  feature/part-1' 
fatal: ambiguous argument '  feature/part-1': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log 'feature/part-1'  
commit b2e05429742e8784eee7dc83b6a9d1fb904988c0 (feature/part-1)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 1

commit d7d09540eb1a24ed1299b230d143e6e93f9807eb (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    init flag printer
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log 'feature/part-2' 
commit e1629c73b55d8831cfa3cda13a74c3e8f7c9e2f1 (feature/part-2)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 2

commit d7d09540eb1a24ed1299b230d143e6e93f9807eb (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    init flag printer
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log 'feature/part-3' 
commit 8fccfcdaeeb259a51b642ba76ec2e5feb086c057 (feature/part-3)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 3

commit d7d09540eb1a24ed1299b230d143e6e93f9807eb (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    init flag printer

```

```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git show b2e05429742e8784eee7dc83b6a9d1fb904988c0
commit b2e05429742e8784eee7dc83b6a9d1fb904988c0 (feature/part-1)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 1

diff --git a/flag.py b/flag.py
index 77d6cec..6e17fb3 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,2 @@
 print("Printing the flag...")
+print("picoCTF{t3@mw0rk_", end='')
\ No newline at end of file
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git checkout feature/part-1
cat <tên_file_chứa_flag>
zsh: parse error near `\n'
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git show e1629c73b55d8831cfa3cda13a74c3e8f7c9e2f1
commit e1629c73b55d8831cfa3cda13a74c3e8f7c9e2f1 (feature/part-2)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 2

diff --git a/flag.py b/flag.py
index 77d6cec..7ab4e25 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,3 @@
 print("Printing the flag...")
+
+print("m@k3s_th3_dr3@m_", end='')
\ No newline at end of file
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git show 8fccfcdaeeb259a51b642ba76ec2e5feb086c057
commit 8fccfcdaeeb259a51b642ba76ec2e5feb086c057 (feature/part-3)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    add part 3

diff --git a/flag.py b/flag.py
index 77d6cec..dfee641 100644
--- a/flag.py
+++ b/flag.py
@@ -1 +1,3 @@
 print("Printing the flag...")
+
+print("w0rk_7ae8dd33}")

```



## Run

. flag picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ae8dd33}



