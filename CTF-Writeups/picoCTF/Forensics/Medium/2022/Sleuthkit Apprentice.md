# 🚩Sleuthkit Apprentice - picoCTF 2022

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `disk.flag.img`
- **Key Skills And Tools:** mmls, fls, icat, reading data
---

## 🔍 Challenge 

Download this disk image and find the flag.

Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

Download compressed disk image

### 🧪 Logic Extraction:

You already know how to extract files, right? This is a disk challenge, so I used the `mmls` command to extract the list inside. Is there anything else?

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mmls disk.flag.img       
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)

```

Next, I used the `fls` command to extract the data from the start column, the last row, and search for the flag name.

```        
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ fls disk.flag.img -o 360448 -r | grep flag
++ r/r * 2082(realloc): flag.txt
++ r/r 2371:    flag.uni.txt

```
Once the flag file name appeared, I used the `icat` command to extract the data from the file, and it displayed the flag.

```
                                                                                                                                                `        
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat disk.flag.img -o 360448 2082 -r   
            3.449677            13.056403
           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat disk.flag.img -o 360448 2371 -r 
picoCTF{by73_5urf3r_2f22df38}

```



## Run 
.flag picoCTF{by73_5urf3r_2f22df38}
