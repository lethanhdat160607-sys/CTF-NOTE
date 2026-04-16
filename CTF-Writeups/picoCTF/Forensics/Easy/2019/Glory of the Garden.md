# 🚩Glory of the Garden - picoCTF 2019

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `pcap file`
- **Key Skills And Tools:** xxd, Convert from image to hexadecimal data
---

## 🔍 Challenge 
This file contains more than it seems. Get the flag from garden.jpg.


### 🧪 Logic Extraction:

Next, we use the `xxd` function to extract the binary data in hexadecimal format.

```
xxd garden.jpg > imge.hex 
```

<div aling="center">
  <img width="650" height="128" alt="image" src="https://github.com/user-attachments/assets/266347a3-7787-4eb8-bd24-2522a4011df2" />
<div>


## Run 
.flag picoCTF{more_than_m33ts_the_3y398ee229a}.

