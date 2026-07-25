# 🚩 Codebook - picoCTF 2023

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `enc_flag`
- **Key Skills And Tools:** cat, base64, reading data file
---

## 🔍 Challenge 

Can you make sense of this file?

Download the file here
.

### 🧪 Logic Extraction:

I used the `cat` command to extract the data.
```
                                                                                                                                                            
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat enc_flag          
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXMTRWMDVHV2toalJYUlhDazFyV25sVVZXaHpWakpHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==


```

Use an online tool to encode base64, equal to 7 times the tool's value.

<div align="center">
  <img width="1054" height="582" alt="image" src="https://github.com/user-attachments/assets/9ec11d6b-aa86-4960-9c3c-7b254342fedc" />


<div>


## Run

. flag picoCTF{c0d3b00k_455157_7d102d7a}


