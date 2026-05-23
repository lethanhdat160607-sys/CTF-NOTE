# 🚩endianness-v2 - picoCTF 2024

- **Category:** Forensics ⚙️
- **Difficulty:** Medium 
- **Target File:** `challengefile`
- **Key Skills And Tools:** strings, reading data
---

## 🔍 Challenge 

Here's a file that was recovered from a 32-bits system that organized the bytes a weird way. We're not even sure what type of file it is.

Download it here and see what you can get out of it

### 🧪 Logic Extraction:


```
new_hex = ""
 
with open("challengefile", "rb") as file:
    hexdata = file.read().hex()
 
hex_chunks = [hexdata[i:i+8] for i in range(0, len(hexdata), 8)]
 
for chunk in hex_chunks:
    for i in range(len(chunk)-2,-1,-2):
        new_hex += chunk[i] + chunk[i+1]
 
with open("solved.jpg", "wb") as file:
    file.write(bytes.fromhex(new_hex))
 
print("File created successfully")
```


## Run 
.flag picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_f72c4bf7}

