# 🚩Wireshark doo dooo do doo... - picoCTF 2021

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `shark1.pcapng`
- **Key Skills And Tools:** wireshark, rot13, reading TCP packets
---

## 🔍 Challenge 

Can you find the flag?
shark1.pcapng

### 🧪 Logic Extraction:

Open the file in Wireshark and type `tcp.stream eq 5` to get the 5th TCP stream and you will see the code `ROT13`.

<div align="center">
   <img width="1355" height="582" alt="image" src="https://github.com/user-attachments/assets/b4552160-08dc-49df-a5d7-a0ab4cfe123f" />

</div>

#

I changed the code to `ROT13`, you can also use `ROT13 online`.

```
┌──(kali㉿kali)-[~/Tools/CTF]
└─$ echo "cvpbPGS{c33xno00_1_f33_h_qrnqorrs}" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
picoCTF{p33kab00_1_s33_u_deadbeef}
                                   
```

## Run 
.flag picoCTF{p33kab00_1_s33_u_deadbeef}

