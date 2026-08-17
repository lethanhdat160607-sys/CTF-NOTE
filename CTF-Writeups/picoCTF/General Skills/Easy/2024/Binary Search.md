# 🚩 Binary Search - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `challenge.zip`
- **Key Skills And Tools:** shhpass, ssh, reading data file
---

## 🔍 Challenge 

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.

Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!

You can download the challenge files here:

challenge.zip
ssh -p 63043 ctf-player@atlas.picoctf.net
Using the password 83dcefb7. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!


### 🧪 Logic Extraction:

I use the `sshpass` command to input the password and guess the number; once I get a hit, I select the middle values ​​to narrow it down based on the "Higher" or "Lower" feedback until I find the flag.

```
┌──(kali㉿kali)-[~/…/Misc/home/ctf-player/drop-in]
└─$ sshpass -p '83dcefb7' ssh -p 64889 ctf-player@atlas.picoctf.net
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Higher! Try again.
Enter your guess: 400
Higher! Try again.
Enter your guess: 450
Lower! Try again.
Enter your guess: 425
Lower! Try again.
Enter your guess: 410
Lower! Try again.
Enter your guess: 405
Higher! Try again.
Enter your guess: 408
Congratulations! You guessed the correct number: 408
Here's your flag: picoCTF{g00d_gu355_ee8225d0}
Connection to atlas.picoctf.net closed.

```

## Run

. flag picoCTF{g00d_gu355_ee8225d0}

