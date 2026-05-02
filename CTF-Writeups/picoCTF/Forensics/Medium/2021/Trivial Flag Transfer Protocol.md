# 🚩Trivial Flag Transfer Protocol - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `tftp.pcapng`
- **Key Skills And Tools:** wireshark, rot13, Information hiding techniques
---

## 🔍 Challenge 

Figure out how they moved the flag.
tftp.pcapng

### 🧪 Logic Extraction:

This challenge involved a packet log file, so I used the `wireshark` command to open it and the TFTP Object List so I could view all the packets transmitted over the network, and then I saved it to my computer.

<div align="center">
  <img width="1316" height="722" alt="image" src="https://github.com/user-attachments/assets/33da2c6a-8dcf-4dd3-bbba-3e12eb41545b" />
</div>

#
I opened the plan file and inside there were some characters that looked like `ROT13`, so I used the command to encode them: `tr 'A-Za-z' 'N-ZA-Mn-za-m'` or you can use `ROT13 online` to encode them.

```
┌──(kali㉿kali)-[~/Tools]
└─$ cat plan            
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF

┌──(kali㉿kali)-[~/Tools]
└─$ echo "VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF" | tr 'A-Za-z' 'N-ZA-Mn-za-m'                                                 
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```
#

Based on the encrypted data in `DUEDILIGENCE` as a password, I used the `steghide extract` command to retrieve the hidden data. `-st` stands for (Source File), and I performed this on the files in the hidden folder: `picture1.bmp`, `picture2.bmp`, `picture3.bmp`. I tried all the files, and `-p` provided the password. After that, the file opened and the flag was visible.

```
┌──(kali㉿kali)-[~/Tools]
└─$ steghide extract -sf picture3.bmp -p DUEDILIGENCE
wrote extracted data to "flag.txt".

┌──(kali㉿kali)-[~/Tools]
└─$ cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

## Run 
.flag picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

