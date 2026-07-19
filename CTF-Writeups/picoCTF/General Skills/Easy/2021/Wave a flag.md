# 🚩 Static ain't always noise - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `warm`
- **Key Skills And Tools:** strings, reading file data
---

## 🔍 Challenge 

Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

warm

### 🧪 Logic Extraction:

I used the `strings` command to open the file and it gave a flag.

```                                                       
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ strings warm | grep picoCTF
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}


```

## Run

. flag picoCTF{d15a5m_t34s3r_20335e41}


