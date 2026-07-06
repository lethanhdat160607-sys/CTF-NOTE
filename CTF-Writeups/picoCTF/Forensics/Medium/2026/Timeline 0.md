# 🚩Timeline 0 - picoCTF 2026

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `partition4.img.gz`
- **Key Skills And Tools:** fls, icat, mactime, reading data
---

## 🔍 Challenge 

Can you find the flag in this disk image? Wrap what you find in the picoCTF flag format.

Download the disk image here.


Download the network capture file: here

### 🧪 Logic Extraction:

I used the  <a href="https://wiki.sleuthkit.org/fls/" target="_blank"> fls </a> command to list the directories in the image file and `-r` to perform a recursive search, listing not only the root directory but also going into every other directory in the disk image. `-m` sets the output mode to Body file format, and `/` directs the root path of the file system in the disk image so that `fls` starts listing and redirects `>body.txt` to a text file instead of directly printing to the screen. 


```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ fls -r -m / partition4.img > body.txt
 
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ ls
body.txt  partition4.img
```

Next, we use the <a href= "https://wiki.sleuthkit.org/mactime/"target="_blank"> mactime </a>
 command, which retrieves a list of raw data and arranges it into a timeline in real-time order. The `-b body.txt` file parameter and the redirection `> timeline.txt` write the entire sorted result to the `timeline.txt` file for easy reference.


```
 ┌──(kali㉿kali)-[~/Tools/CTF1]
 └─$ mactime -b body.txt > timeline.txt
 Old package separator "'" deprecated at /usr/bin/mactime line 154.
 Old package separator "'" deprecated at /usr/bin/mactime line 167.
                                                                                                                                                           
```

<div align="center">
  <img width="1339" height="303" alt="image" src="https://github.com/user-attachments/assets/b024ed6d-bf5b-4ba6-8449-3bb31888029a" />

</div>



```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 4945

NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ echo "NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK" | base64 -d
71m311n3_0u7113r_h3r_43a2e7af

```

## Run 
.flag picoCTF{71m311n3_0u7113r_h3r_43a2e7af}



