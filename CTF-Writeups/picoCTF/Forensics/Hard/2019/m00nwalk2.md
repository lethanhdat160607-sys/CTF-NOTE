# 🚩m00nwalk2 - picoCTF 2019

- **Category:** Forensics ⚙️
- **Difficulty:** Hard
- **Target File:** `clue1.wav`, `clue2.wav`, `clue3.wav`, `message.wav`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

Revisit the last transmission. We think this transmission
 contains a hidden message. There are also some clues clue 1
, clue 2
, clue 3
.

### 🧪 Logic Extraction:

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sstv -d message.wav -o message.png

┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sstv -d clue1.wav -o clue1.png

┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sstv -d clue2.wav -o clue2.png

┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ sstv -d clue3.wav -o clue3.png
```

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ eog *.png 
```
<img width="468" height="321" alt="image" src="https://github.com/user-attachments/assets/b3f73232-5577-4a68-b922-111fad068d99" />

<img width="471" height="320" alt="image" src="https://github.com/user-attachments/assets/429d7f81-1ed2-4546-8963-ef59a5957d1a" />

<img width="466" height="320" alt="image" src="https://github.com/user-attachments/assets/e8e190b2-e92d-4bf2-9902-f7ffc953f040" />

<img width="466" height="317" alt="image" src="https://github.com/user-attachments/assets/c59c255e-110b-45d8-b605-7cd520612bdd" />

#

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ steghide extract -sf message.wav -p hidden_stegosaurus  
wrote extracted data to "steganopayload12154.txt".
```

```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ cat steganopayload12154.txt
picoCTF{the_answer_lies_hidden_in_plain_sight}
```


## Run 
.flag picoCTF{the_answer_lies_hidden_in_plain_sight}


