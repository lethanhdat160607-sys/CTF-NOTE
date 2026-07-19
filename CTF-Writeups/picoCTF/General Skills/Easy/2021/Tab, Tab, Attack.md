# 🚩 Tab, Tab, Attack - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `Addadshashanammu.zip`
- **Key Skills And Tools:** unzip, cat, reading file data
---

## 🔍 Challenge 

Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames.

Addadshashanammu.zip

### 🧪 Logic Extraction:

I used the `unzip` command to extract the file.

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ unzip Addadshashanammu.zip
Archive:  Addadshashanammu.zip
   creating: Addadshashanammu/
   creating: Addadshashanammu/Almurbalarammi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
 extracting: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet.c  
  inflating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet  

```

I used the `cat` command to access and read data from files to generate the flag.

```                                                       
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet.c           
#include <stdio.h>

int main(){
printf("*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}\n");
 have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}

```


## Run

. flag picoCTF{d15a5m_t34s3r_20335e41}


