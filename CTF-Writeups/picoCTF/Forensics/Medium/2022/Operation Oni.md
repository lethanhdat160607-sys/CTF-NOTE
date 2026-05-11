# 🚩Operation Oni - picoCTF 2022

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `disk.img`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

Download this disk image, find the key and log into the remote machine.

Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

Download disk image
Remote machine: `ssh -i key_file -p 49406 ctf-player@saturn.picoctf.net`

### 🧪 Logic Extraction:

I used the tool `autopsy` to retrieve files hidden on the disk.

<div align="center">
   <img width="359" height="557" alt="image" src="https://github.com/user-attachments/assets/f3d8932f-3d06-4101-9313-9b8552f88892" />
</div>

#
I opened it and found an `ssh` file. Since it contained a `ssh` and `server` string, I used it to generate a key to access the server.

<div align="center">
   <img width="998" height="615" alt="image" src="https://github.com/user-attachments/assets/4bfb81b2-b7a4-4823-931a-82f9270b2077" />


</div>

#
This is the key to log into the server, and please remember the code to avoid misinterpreting it; it's shown on lines 8 and 9.
<div align="center">
   <img width="693" height="383" alt="image" src="https://github.com/user-attachments/assets/12b26e33-25ed-4803-8c3f-f417085f8594" />

</div>

#
I used the `chmod 600` command to grant the highest possible permissions to your server. 
document: https://mangohost.net/blog/chmod-600-specific-permission-setting/
```
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ chmod 600 key_file 

```

Once you've logged into the server, use the `ls` command to view the list and retrieve the flags.

<div align="center">
   <img width="967" height="355" alt="image" src="https://github.com/user-attachments/assets/9b665428-efbc-47b6-9afb-8744cf8274ef" />

</div>

## Run 
.flag picoCTF{k3y_5l3u7h_b5066e83}

