# 🚩WebNet1 - picoCTF 2019

- **Category:** Forensics ⚙️
- **Difficulty:** Hard
- **Target File:** `capture.pcap`, `picopico.key`
- **Key Skills And Tools:** wireshark, http, hexdump, key, reading data network
---

## 🔍 Challenge 

We found this packet capture
 and key
. Recover the flag.

### 🧪 Solution
After downloading the file, we check whether it uses a public or private key; it appears to be a private file. This is crucial for accessing encrypted traffic.
```
┌──(kali㉿kali)-[~/Tools/Forensic]
└─$ strings picopico.key                           
-----BEGIN PRIVATE KEY-----
MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCwKlFPNKjseJF5
puCJU5x38XcT1eQge5zOKNahAlYudvGVOEs61TnIgvcER4ko8i3OCwak2/atcGk3
oz9jFKep7XFEYNP31IwwD9j/YazlKy4DRLGObOyIZUU1f2WRA7Uhf0POQXsDT1oU
X32jMKZkQSSDW4MRZd9trJYdO2TrcEPMsBiZQlFlvgnNwl3QlawozTHLAJKI36j1
cPwSMMeNca1e0Zi1s7R5IxfhpNXOBF0FmxiWvmeOHbaspyHg8UEmGBrkd4k4wXSK
GQvrc8QjycP4ScEdquxJiYnDT8iEbAq70/7f/5NIN1DE9YoGJqKYjTS9nRPB4Yvj
JN/SJnhvAgMBAAECggEACCnd3LrG/TZVH3sROqvqO1CwQPYPfUXdLVyNHab7EWon
pc+XBOHurJENG2CpRYF7h+nQ5ADhfIYSCicBf/jsEB7VueJ20CxEVtHVL3h6R6Bp
oHMle0Em8OcofuMpdL/kO+om3T8BkVSzCvCl5NMTUuAF7iRmfX7oDLALwM0IzzQv
2un+2UmT15rgAZfl3IL1PGvJhbhLxfeeyPE9MBy1SqBjQ9rNFn8sQv959J6BHz4b
EpK//ErtNP2yh7oiVBBgKEQ1gEuOjQC/4oxoqCFfZaf9XNRCxB/zY1nUprvJyz09
NMQWNF2EmvmBVGfoTxmuut5N0GbVr2UyHxWMKm2sOQKBgQDpb2+AWgWlGtetuLKJ
fJs8dnd6LhnafbKCOXMOT68qMBRoTpBtVTLRVSNvWCm8m4TTEazX4+ZA+bJFwUFw
aATDmHcr6lMI3tNKrcsnY2F7o5I4z6mwuRuSeszq/ndxZqCzwCu4nKixh3cznp7j
JiElNG0d8Lu5eQgmVAK1AhWXfQKBgQDBMa9ga7VJUP4pzcHnWAoi34OpfjvQYeGl
IKL3AKO4OedaHdH9qid41PQHnL7O3xzN669SkLZ5s0d88A/LFLk4oZNMKdkSTQIQ
+AMbXH01HGFvnCOuPg/FbNp1wS7zJEg5u5HFQWyMPNJLr/hZ6g2Yp+UGpAcGTwM/
RCPVAPhLWwKBgQDAB0OaOnPaVjKGXiHAqBirrGiswa/S5QQrzEaxxys5cUPYaoi0
6BldysPTnJr45JZna2rcTkXjvYTBjTDf3zHMFWgzYBfefC8kh8NPK5nNs8ldorbd
AemEnjBkP+DSELKyK6vLulOrdtzAQgRCp+MsT+xTbO2ArefeX826SXSpoQKBgC2v
nDOHBQXje1dTawlUToFUrgQE8AwlOYEdKKyUoCLOvqEW8DO2a0MtyM+MB6tQI7Wm
iH1T73L0LHGlK3bw3aRAwV5/fu/O+jAdFk8AHjPTFE+acu2fi4c6aKb0GjAxYksU
yjIFeK/pKinv4SESMkjpW0WowGiDgtcRPBAA/LaFAoGAfEM1rfM0v3UmB7PS6u0m
P3ckP2CFCdaryXPfC52GBcJ3Q46YpsQvLTVotM+teHvTjNw2jwwZxIl4NenGSEj3
KDhQoOiQC9BrDD+DB4I9+T9nxT3g7R6MrgITghB4We7TVhL/PljnJTyDqpjNA4kY
TveAJPv6Xq1ERt5PUtX3BqQ=
-----END PRIVATE KEY-----

```
Next, we open the pcap file containing TLS traffic in Wireshark; the traffic will be unreadable because it is encrypted.
<div align="center">
 <img width="1320" height="553" alt="image" src="https://github.com/user-attachments/assets/708c04a2-b515-437e-bd32-211055b30fe3" />

</div>

#
However, we are provided with a private key file that can be used with the traffic. In Wireshark, go to Edit > Preferences > Protocols > TLS. Click the “Edit” button under “RSA keys list,” then add picopico.key and click OK. This step allows us to decrypt the encrypted data packets.
<div align="center">
  <img width="1365" height="725" alt="image" src="https://github.com/user-attachments/assets/f4a35c57-43b0-48b6-b910-220440126440" />

</div> 

#
After adding the encryption key, we can return to the packet capture display and view the decrypted packets. We can now see the HTTP packets exchanged between 128.237.140.23 and 172.31.22.220.
<div align="center">
  <img width="1344" height="569" alt="image" src="https://github.com/user-attachments/assets/c35445f3-36a1-4e00-93c2-21230e6326f2" />

</div> 

#
The first HTTP packet is a GET request for /second.html. In the HTTP header, there is a Pico-Flag—picoCTF{this.is.not.your.flag.anymore}—which I naturally tried, but it wasn't the correct flag 😅.
<div align="center">
 <img width="1337" height="748" alt="image" src="https://github.com/user-attachments/assets/ad8c685b-8bfb-401e-8d13-4a1e26b40522" />
</div>

#
Subsequent HTTP streams include additional GET requests for files, including an image named /vulture.jpg. Instead of tracking each stream individually, let's extract all HTTP stream files from the capture. In Wireshark, go to File > Export Objects > HTTP and save the files listed there.
<div align="center">
 <img width="1358" height="604" alt="image" src="https://github.com/user-attachments/assets/6e31b6b9-2698-4d2b-b3a7-f1a593ba6263" />
  <img width="815" height="113" alt="image" src="https://github.com/user-attachments/assets/23ff0a6c-58f3-47c4-a121-0eeb558ca630" />

</div>

#
Now, open `second.html`, as the other files appear to be supporting data.
<div align="center">
 <img width="634" height="637" alt="image" src="https://github.com/user-attachments/assets/4dbe08cb-f7bf-4870-ba27-27cc2db145fc" />

</div>

#

Next, when examining the image, I checked for steganography techniques and used the `hexdump` command to see if anything was hidden behind the image data—and I discovered the flag right away.
```
┌──(kali㉿kali)-[~/Tools/Forensic]
└─$ hexdump -C vulture.jpg | less

```

<div align="center">
  <img width="675" height="265" alt="image" src="https://github.com/user-attachments/assets/71df3324-7961-4c50-9d08-89ef4a60fecf" />

</div>
 
## Run
.flag picoCTF{honey.roasted.peanuts}

