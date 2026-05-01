# 🚩Wireshark twoo twooo two twoo... - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `shark2.pcapng`
- **Key Skills And Tools:**  wireshark, tshark, 
---

## 🔍 Challenge 


Can you find the flag?
shark2.pcapng

### 🧪 Logic Extraction:

I used the `wireshark` command to read the packets and I saw quite a lot of `HTTP` and web links, so I opened the HTTP object list and saw a flag file, but there were so many of them that I guessed it was just a dummy flag.

<div align="center"> 
  <img width="1361" height="575" alt="image" src="https://github.com/user-attachments/assets/98c29adb-0192-4c38-b301-4b0023db066c" />
</div>

#

I use the `tshark` command to analyze network traffic. `-nr` reads the stored data file (`-r`) without reversing the domain name (`-n`) for faster reading speed, while `-Y 'dns'` applies a display filter, keeping only packets belonging to the DNS protocol.

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns'
```
Next, I used the command `grep -v '8.8.8.8'`, where `-v` removes the lines containing the string after the '8.8.8.8', and `8.8.8.8` removes packets related to Google's DNS (8.8.8.8) to reduce unnecessary data noise.

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' 
```
Next, I use the `grep -v response` command in DNS to get the query and response packets. Here, we are only interested in what the client sends, so we remove the lines containing the word "response" to make the page the response data to the server.
```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' | grep -v response
```
Next, use the `grep local` command to filter out lines containing the word "local". In this lab, the secret data is hidden in queries sent to domains ending in `.local`.

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' | grep -v response | grep local
```

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' | grep -v response | grep local | awk '{print $12}'
```

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' | grep -v response | grep local | awk  '{print $12}' | sed  's/\..*//' 
```

```
┌──(kali㉿kali)-[~/Tools]
└─$ tshark -nr shark2.pcapng -Y 'dns' | grep -v '8.8.8.8' | grep -v response | grep local | awk  '{print $12}' | sed  's/\..*//' | base64 -d
picoCTF{dns_3xf1l_ftw_deadbeef}}
```
## Run 
.flag picoCTF{dns_3xf1l_ftw_deadbeef}}                                                                                                                                                           
