# 🚩 Static ain't always noise - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `ltdis.sh`, `static`
- **Key Skills And Tools:** strings, reading file data
---

## 🔍 Challenge 

Can you look at the data in this binary? The bash script might help!

static
, ltdis.sh

### 🧪 Logic Extraction:

I used the `strings` command to open the file and it gave a flag.

```                                                       

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ strings static | grep pico
picoCTF{d15a5m_t34s3r_20335e41}

```

## Run

. flag picoCTF{d15a5m_t34s3r_20335e41}


