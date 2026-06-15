# 🚩Bitlocker-1 - picoCTF 2025

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `bitlocker-1.dd`
- **Key Skills And Tools:** file, bitlocker2john, bdemount, reading data disk
---

## 🔍 Challenge 

Jacky is not very knowledgable about the best security passwords and used a simple password to encrypt their BitLocker drive. See if you can break through the encryption!

Download the disk image here                                                                                                                                                    


### 🧪 Logic Extraction:

I used the `file` command to investigate and found that this file likely contains data from a Windows NTFS-formatted partition, which has been locked by BitLocker, identifiable by the `-FVE-FS` signature.
```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ file bitlocker-1.dd

bitlocker-1.dd: DOS/MBR boot sector, code offset 0x58+2, OEM-ID "-FVE-FS-", sectors/cluster 8, reserved sectors 0, Media descriptor 0xf8, sectors/track 63, heads 255, hidden sectors 124499968, FAT (32 bit), sectors/FAT 8160, serial number 0, unlabeled; NTFS, sectors/track 63, physical drive 0x1fe0, $MFT start cluster 393217, serial number 02020454d414e204f, checksum 0x41462020

```                                                                                                                                                   
I used the `bitlocker2john` tool to extract the encryption data from the drive and wrote it to the `bitlocker.hash` file. 

The information obtained includes `Version: 2 (Windows 7 or later)`:, indicating the drive uses a modern encryption structure from Windows 7 onwards.

`VMK encrypted with Recovery Password`: This drive can be unlocked using a 48-digit random recovery password from Windows.

`VMK encrypted with User Password`: This drive can also be unlocked using a regular user-set password.                                                                                                                                                   
```                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ bitlocker2john -i bitlocker-1.dd > bitlocker.hash

Signature found at 0x3
Version: 8 
Invalid version, looking for a signature with valid version...

Signature found at 0x2195000
Version: 2 (Windows 7 or later)

VMK entry found at 0x21950c5

VMK encrypted with Recovery Password found at 0x21950e6
Searching AES-CCM from 0x2195102
Trying offset 0x2195195....
VMK encrypted with AES-CCM!!

VMK entry found at 0x2195241

VMK encrypted with User Password found at 2195262
VMK encrypted with AES-CCM

Signature found at 0x2c1d000
Version: 2 (Windows 7 or later)

VMK entry found at 0x2c1d0c5

VMK entry found at 0x2c1d241

Signature found at 0x373a000
Version: 2 (Windows 7 or later)

VMK entry found at 0x373a0c5

VMK entry found at 0x373a241

```

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ cat bitlocker.hash
Encrypted device bitlocker-1.dd opened, size 100MB
Salt: 2b71884a0ef66f0b9de049a82a39d15b
RP Nonce: 00be8a46ead6da0106000000
RP MAC: a28f1a60db3e3fe4049a821c3aea5e4b
RP VMK: a1957baea68cd29488c0f3f6efcd4689e43f8ba3120a33048b2ef2c9702e298e4c260743126ec8bd29bc6d58

UP Nonce: d04d9c58eed6da010a000000
UP MAC: 68156e51e53f0a01c076a32ba2b2999a
UP VMK: fffce8530fbe5d84b4c19ac71f6c79375b87d40c2d871ed2b7b5559d71ba31b6779c6f41412fd6869442d66d


User Password hash:
$bitlocker$0$16$cb4809fe9628471a411f8380e0f668db$1048576$12$d04d9c58eed6da010a000000$60$68156e51e53f0a01c076a32ba2b2999afffce8530fbe5d84b4c19ac71f6c79375b87d40c2d871ed2b7b5559d71ba31b6779c6f41412fd6869442d66d
Hash type: User Password with MAC verification (slower solution, no false positives)
$bitlocker$1$16$cb4809fe9628471a411f8380e0f668db$1048576$12$d04d9c58eed6da010a000000$60$68156e51e53f0a01c076a32ba2b2999afffce8530fbe5d84b4c19ac71f6c79375b87d40c2d871ed2b7b5559d71ba31b6779c6f41412fd6869442d66d
Hash type: Recovery Password fast attack
$bitlocker$2$16$2b71884a0ef66f0b9de049a82a39d15b$1048576$12$00be8a46ead6da0106000000$60$a28f1a60db3e3fe4049a821c3aea5e4ba1957baea68cd29488c0f3f6efcd4689e43f8ba3120a33048b2ef2c9702e298e4c260743126ec8bd29bc6d58
Hash type: Recovery Password with MAC verification (slower solution, no false positives)
$bitlocker$3$16$2b71884a0ef66f0b9de049a82a39d15b$1048576$12$00be8a46ead6da0106000000$60$a28f1a60db3e3fe4049a821c3aea5e4ba1957baea68cd29488c0f3f6efcd4689e43f8ba3120a33048b2ef2c9702e298e4c260743126ec8bd29bc6d58
****
```

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ john --wordlist=rockyou.txt bitlocker.hash
Note: This format may emit false positives, so it will keep trying even after finding a possible candidate.
Using default input encoding: UTF-8
Loaded 2 password hashes with 2 different salts (BitLocker, BitLocker [SHA-256 AES 32/64])
Cost 1 (iteration count) is 1048576 for all loaded hashes
Will run 2 OpenMP threads
 Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:01 0.00% (ETA: 2026-07-17 12:02) 0g/s 3.921p/s 9.803c/s 9.803C/s iloveyou..princess
0g 0:00:00:02 0.00% (ETA: 2026-07-18 20:26) 0g/s 5.000p/s 10.00c/s 10.00C/s nicole..daniel
0g 0:00:04:58 0.01% (ETA: 2026-08-02 12:04) 0g/s 4.280p/s 8.568c/s 8.568C/s tiger..hotgirl
0g 0:00:04:59 0.01% (ETA: 2026-08-02 12:01) 0g/s 4.279p/s 8.565c/s 8.565C/s cuties..valentine
jacqueline       (?)     
jacqueline       (?)  
```

They created the `/mnt/bitlocker` directory simply as an empty shell. When the `bdemount` command is run, all the contents (files, directories, and the flag.txt file) hidden inside the `bitlocker-1.dd` file are "dumped" into and displayed through this empty shell directory.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sudo mkdir /mnt/bitlocker
[sudo] password for kali: 
mkdir: cannot create directory ‘/mnt/bitlocker’: File exists

      
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sudo bdemount -p 'jacqueline' bitlocker-1.dd /mnt/bitlocker
bdemount 20240502
```
```                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sudo su
```
```
┌──(root㉿kali)-[/home/kali/Tools/CTF1]
└─# ls -la                     
total 102424
drwxrwxr-x 2 kali kali      4096 Jun 11 23:52 .
drwxrwxr-x 5 kali kali     12288 Jun 11 23:48 ..
-rw-rw-r-- 1 kali kali 104857600 Mar  6  2025 bitlocker-1.dd
-rw-rw-r-- 1 kali kali      1510 Jun 11 23:53 bitlocker.hash
```
```                                                                                                                                                            
┌──(root㉿kali)-[/home/kali/Tools/CTF1]
└─# cd /mnt/extracted_files
```
```           
┌──(root㉿kali)-[/mnt/extracted_files]
└─# ls -la
total 13
drwxrwxrwx 1 root root 4096 Jul 15  2024  .
drwxr-xr-x 4 root root 4096 Jun 11 22:25  ..
drwxrwxrwx 1 root root    0 Jul 15  2024 '$RECYCLE.BIN'
-rwxrwxrwx 1 root root   43 Jul 15  2024  flag.txt
drwxrwxrwx 1 root root 4096 Jul 15  2024 'System Volume Information'
```
```                                                                                                                                                            
┌──(root㉿kali)-[/mnt/extracted_files]
└─# cat /mnt/extracted_files/flag.txt
picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1} 
```
## Run 
.flag picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1}                                                                                                                                                            

