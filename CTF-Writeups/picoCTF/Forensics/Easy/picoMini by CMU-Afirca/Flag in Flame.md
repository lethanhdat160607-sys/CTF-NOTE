# 🚩Flag in Flame - picoMini by CMU-Afirca 

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `logs.txt`
- **Key Skills And Tools:** hexedit, mv, xxd, png, Identification mark
---

## 🔍 Challenge 

The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log.
Download the encoded data here: Logs Data. Be prepared—the file is large, and examining it thoroughly is crucial .

### 🧪 Logic Extraction:

Based on my analysis, these codes are in hex, with the first digits being `6956`, `424f`. Therefore, I changed it to `8950` `4e47`. I checked the documentation and found that the format at the beginning of a `PNG` file is `8950` `4E47`, which is quite familiar. Actually, encoding in `PNG` or `JPEG` is fine; it doesn't affect much since it's just an image. However, I recommend using `PNG` for better results, as it provides an indicator to always change the `base64` encoding to `PNG` when encountering problems.

<div align="center"> 
  <img width="778" height="305" alt="image" src="https://github.com/user-attachments/assets/1a429781-a308-4c0d-b14a-cc244de6b125" />
</div>

#
Check further using the `strings` command.
<div align="center">
  <img width="1338" height="203" alt="image" src="https://github.com/user-attachments/assets/cb5715e5-7e49-4451-97ad-f16d065450cf" />
  <p> There are signs of base64.</p>
  <img width="1337" height="293" alt="image" src="https://github.com/user-attachments/assets/4b978e6c-151c-4dac-8870-931f46bb03e4" />
  <p> There are signs of base64.</p>
</div> 

Use the base64 command to convert `file.txt` to `JPEG`.
```
┌──(kali㉿kali)-[~/Tools]
└─$ base64 -d logs.txt > flag.jpeg
```

change hex `7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F62396163346362397D`
is the flag

## Run 
.flag picoCTF{forensics_analysis_is_amazing_b9ac4cb9}
