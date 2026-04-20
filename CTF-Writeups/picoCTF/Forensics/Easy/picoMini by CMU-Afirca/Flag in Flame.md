# 🚩Flag in Flame - picoMini by CMU-Afirca 

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `logs.txt`
- **Key Skills And Tools:** hexedit, mv, xxd, jpeg, Identification mark
---

## 🔍 Challenge 

The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log.
Download the encoded data here: Logs Data. Be prepared—the file is large, and examining it thoroughly is crucial .

### 🧪 Logic Extraction:

<div align="center"> 
  <img width="778" height="305" alt="image" src="https://github.com/user-attachments/assets/1a429781-a308-4c0d-b14a-cc244de6b125" />
</div>


<div align="center">
  <img width="1338" height="203" alt="image" src="https://github.com/user-attachments/assets/cb5715e5-7e49-4451-97ad-f16d065450cf" />

  <img width="1337" height="293" alt="image" src="https://github.com/user-attachments/assets/4b978e6c-151c-4dac-8870-931f46bb03e4" />

</div> 




```
┌──(kali㉿kali)-[~/Tools]
└─$ base64 -d logs.txt > flag.jpeg
```
`7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F62396163346362397D`


## Run 
.flag picoCTF{forensics_analysis_is_amazing_b9ac4cb9}
