# 🚩flags are stepic - picoCTF 2025

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `http://standard-pizzas.picoctf.net:54036/`
- **Key Skills And Tools:** stepic, reading data img 
---

## 🔍 Challenge 

A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message

Try it here!

### 🧪 Logic Extraction:

The challenge led me to a website with flags of many countries around the world, and when one flag appeared, I tried downloading that image file.

<div align="center"> 
  <img width="1362" height="684" alt="image" src="https://github.com/user-attachments/assets/37358e7c-c1aa-45b1-91ac-f203385ef552" />
</div>

I used the `stepic` command, which is used to hide data within image files without significantly altering them. `-d` instructs the tool to decrypt and extract the hidden data instead of hiding it. `-i` is the input to provide the file containing the secret information you want to retrieve.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ ls
upz.png
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ stepic -d -i upz.png                           
/usr/lib/python3/dist-packages/PIL/Image.py:3451: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4g0e590975}  

```

## Run 
.flag picoCTF{fl4g_h45_fl4g0e590975}                                                                                                                                                           


