# 🚩 Commitment Issues - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `challenge.zip`
- **Key Skills And Tools:** git, cat, reading data file
---

## 🔍 Challenge 

I accidentally wrote the flag down. Good thing I deleted it!

You download the challenge files here:

challenge.zip

### 🧪 Logic Extraction:

I used the `unzip` command to extract the archive, accessed the `drop-in` file, and used the `cat` command to check if the file contained any data.

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ unzip challenge.zip

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ ls
challenge.zip  drop-in
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cd drop-in
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ ls
message.txt
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ cat message.txt

TOP SECRET
            
```
- I used the `git init` command to initialize the current directory as a Git repository. This command does not result in data loss; it simply ensures that Git is tracking the directory: `Reinitialized existing Git repository in /home/kali/Tools/Misc/drop-in/.git/`

- I use the `git branch -a` command to list all branches in the repository—both local and remote; currently, there is only the `master` branch, and you are currently on that branch, as indicated by the asterisk.

- I use the command `git log --all --oneline` to display the commit history in a condensed format, with the `--all` parameter ensuring that all branches containing commit messages are shown.

```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git init                                              
Reinitialized existing Git repository in /home/kali/Tools/Misc/drop-in/.git/
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git branch -a 
* master
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log --all --oneline
42942c9 (HEAD -> master) remove sensitive info
b562f0b create flag


```
Using the `git log -p -n 5` command you just ran is a powerful technique for extracting information: `git log` displays the commit history; `p` (short for `--patch`) shows detailed diff content—key to revealing what was hidden or changed; and `-n 5` limits the output to the five most recent commits.

```
┌──(kali㉿kali)-[~/Tools/Misc/drop-in]
└─$ git log -p -n 5
commit 42942c9c605b30100f5d859ef6e172027447c0db (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:23 2024 +0000

    remove sensitive info

diff --git a/message.txt b/message.txt
index 0e0fefc..d552d1e 100644
--- a/message.txt
+++ b/message.txt
@@ -1 +1 @@
-picoCTF{s@n1t1z3_c785c319}
+TOP SECRET

commit b562f0b425907789d11d2fe2793e67592dc6be93
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:23 2024 +0000

    create flag

diff --git a/message.txt b/message.txt
new file mode 100644
index 0000000..0e0fefc
--- /dev/null
+++ b/message.txt
@@ -0,0 +1 @@
+picoCTF{s@n1t1z3_c785c319}****

```



## Run

. flag -picoCTF{s@n1t1z3_c785c319}


