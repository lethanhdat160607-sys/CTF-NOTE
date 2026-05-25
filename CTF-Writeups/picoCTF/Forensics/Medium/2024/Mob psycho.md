# 🚩Mob psycho - picoCTF 2024

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `mobpsycho.apk`
- **Key Skills And Tools:**  tree, file, mv, hex, reading data 
---

## 🔍 Challenge 

Can you handle APKs?

Download the android apk here.

### 🧪 Logic Extraction:

This challenge downloaded an APK file for me, and extracting it was a hassle, so I converted it to a zip file for easier extraction.

```        
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mv mobpsycho.apk mobpsycho.zip

┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ ls
AndroidManifest.xml  classes2.dex  classes3.dex  classes.dex  META-INF  mobpsycho.zip  res  resources.arsc


```
I used the `tree` command to extract the `-a` files and hidden files, but I couldn't find the flag file.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tree -a META-INF 
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tree -a META-INF | grep flag

```
I used the `tree` command to extract the files and also used `grep flag` to search for keywords, and it showed the link to the flag.txt file.
```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tree res | grep flag
│   ├── flag.txt


```

Next, I used the `tree` command to extract more files, but I added `-f` to access the full file and `-a` to access hidden files. Once I got the clear file path, I used the `cat` command to access it, and it produced some kind of code.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tree -f -a res | grep flag
│   ├── res/color/flag.txt
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ cat res/color/flag.txt 

7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f62313132616535377d

```
The code looked quite similar to hex code, so I translated it using Cyberchef and got the flag.

<div align="center">
 <img width="1062" height="553" alt="image" src="https://github.com/user-attachments/assets/9e80e10c-633d-4838-b8e0-28a4e2a9904f" />
 
</div>

## Run 
.flag picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_b112ae57}

