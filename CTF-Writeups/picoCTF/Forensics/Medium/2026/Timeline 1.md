# 🚩Timeline  - picoCTF 2026

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `partition4.img.gz`
- **Key Skills And Tools:** strings, reading data
---

## 🔍 Challenge 

Can you find the flag in this disk image? Wrap what you find in the picoCTF flag format.

Download the disk image here.

### 🧪 Logic Extraction:

I used the  <a href="https://wiki.sleuthkit.org/fls/" target="_blank"> fls </a> command to list the directories in the image file and `-r` to perform a recursive search, listing not only the root directory but also going into every other directory in the disk image. `-m` sets the output mode to Body file format, and `/` directs the root path of the file system in the disk image so that `fls` starts listing and redirects `>body.txt` to a text file instead of directly printing to the screen. 

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ fls -r -m / partition4.img > body.txt
 ```
Next, we use the <a href= "https://wiki.sleuthkit.org/mactime/" target="_blank"> mactime </a>
 command, which retrieves a list of raw data and arranges it into a timeline in real-time order. The `-b body.txt` file parameter and the redirection `> timeline.txt` write the entire sorted result to the `timeline.txt` file for easy reference.
```                                                                                                                                                          
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt > timeline.txt
Old package separator "'" deprecated at /usr/bin/mactime line 154.
Old package separator "'" deprecated at /usr/bin/mactime line 167.
                                                                                                                                                           
```
I used the `mactime -b` command to convert a dry list of files into a timeline of events, making it easier to trace the attack on the system. It creates a `body file` timeline that sorts the times.

```                                                                                                                                                                                  
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt  
```
I used the command `mactime -b body.txt` to output a list of all events in chronological order, and `| grep macb` to filter and only display lines containing the string `macb`. This helps you remove redundant lines and focus on files with metadata changes (Modify, Access, Change, Birth) to find clues faster.

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ mactime -b body.txt | grep macb

```

<div align="center">
  <img width="1363" height="536" alt="image" src="https://github.com/user-attachments/assets/39799a59-3fb6-4a4f-bb24-12786d1ff8a0" />

</div>  

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 9   

                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 4943

poweroff
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 33020

shutdown                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 32716

NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK
                                                                                                                                                   
```
```

┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ icat partition4.img 32716 | base64 -d

573417h13r_7h4n_7h3_1457_58527bb222
```


## Run 
.flag picoCTF{573417h13r_7h4n_7h3_1457_58527bb222}




