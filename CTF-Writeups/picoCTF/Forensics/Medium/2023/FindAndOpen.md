# 🚩FindAndOpen.md - picoCTF 2023

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `dump.pcap`,  `flag.zip`
- **Key Skills And Tools:** tshark, string, base64, hex, reading data
---

## 🔍 Challenge 

Someone might have hidden the password in the trace file.

Find the key to unlock this file. This tracefile might be good to analyze.

### 🧪 Logic Extraction:

After you've finished downloading, you'll find a zip file that requires a password and a data packet. I used the `wireshark` tool to view the data and found a very suspicious section: `eth.type == 0x4c4b`. I then examined the data.

<div align="center">
  <img width="1365" height="401" alt="image" src="https://github.com/user-attachments/assets/2e5aa5e1-f168-4ca3-a0ea-38ec56cfc178" />

</div>

#
I used the Cyberchef tool to convert the data to hex and base64 code, and then I got a code that seemed to be a password; entering it would produce a flag.

<div align="center">

  <img width="1058" height="402" alt="image" src="https://github.com/user-attachments/assets/d6adac6e-a5b0-416b-9c3f-4ebefa8f0164" />
  <p> Cyberchef </p>
</div>

#

Another way is to use the command `tshark -r dump.pcap -Y 'eth.type == 0x4c4b' -T fields -e data.data | uniq | xxd -r -p | base64 -d` to try filtering packets belonging to the `0x4c4b` protocol, `uniq` avoids data duplication, `xxd -r -p` converts hex data to binary format, and `base64 -d` converts base64 encoding to get the password for the zip file.

```
tshark -r dump.pcap -Y 'eth.type == 0x4c4b' -T fields -e data.data | uniq | xxd -r -p | base64 -d
This is the secret: picoCTF{R34DING_LOKd_                                                                                                                                                           
```

#
Then we enter the password and open the file to get the flag.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ unzip flag.zip 
Archive:  flag.zip
[flag.zip] flag password: 
 extracting: flag                    
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ ls
dump.pcap  flag  flag.zip
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ cat flag     
picoCTF{R34DING_LOKd_fil56_succ3ss_cbf2ebf6}

```


## Run 
.flag picoCTF{R34DING_LOKd_fil56_succ3ss_cbf2ebf6}

