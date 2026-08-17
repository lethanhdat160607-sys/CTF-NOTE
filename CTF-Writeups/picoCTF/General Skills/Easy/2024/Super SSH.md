# 🚩 Super SSH - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `ssh ctf-player@titan.picoctf.net -p 58431`
- **Key Skills And Tools:** git, cat, reading data file
---

## 🔍 Challenge 

Using a Secure Shell (SSH) is going to be pretty important.

Can you ssh as ctf-player to titan.picoctf.net at port 58431 to get the flag?

You'll also need the password f3b61b38. If asked, accept the fingerprint with yes.

If your device doesn't have a shell, you can use: 
https://webshell.picoctf.org

If you're not sure what a shell is, check out our Primer: 
https://primer.picoctf.com/#_the_shell

### 🧪 Logic Extraction:

Access the server and enter the password believed to contain the flag.
```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ ssh ctf-player@titan.picoctf.net -p 58431
The authenticity of host '[titan.picoctf.net]:58431 ([3.139.174.234]:58431)' can't be established.
ED25519 key fingerprint is: SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:58431' (ED25519) to the list of known hosts.
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
Connection to titan.picoctf.net closed.

```


## Run

. flag picoCTF{s3cur3_c0nn3ct10n_3e293eea}
