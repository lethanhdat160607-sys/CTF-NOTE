# 🚩 keygenme-py - picoCTF 2021

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium 
- **Target File:** `keygenme-trial.py`
- **Key Skills And Tool:** Static Analysis, Python Scripting, SHA256 Hashing

---

## 🔍 Challenge 
In this challenge, we are provided with a Python script called keygenme-trial.py. It acts as a trial version of an "Arcane Calculator." To unlock the full version and reveal the flag, we must reverse-engineer the license key verification logic.


### 🧪 Logic Extraction:
By tracing the `if` statements in the code, I identified the exact indices required from the hex-digest of the hash:

```
        if key[i] != hashlib.sha256(username_trial).hexdigest()[4]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[5]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[3]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[6]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[2]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[7]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[1]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[8]:
            return False
```
---

## 💻 The Solver (Python Script)
Instead of manual calculation, I wrote an automation script to generate the dynamic part and reconstruct the full flag:

```python
import hashlib
from cryptography.fernet import Fernet
import base64

username_trial =b"BENNETT"
bUsername_trial = b"BENNETT"

key_part_static1_trial = "picoCTF{1n_7h3_kk3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"
key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

print(hashlib.sha256(username_trial).hexdigest()[4])
print(hashlib.sha256(username_trial).hexdigest()[5])
print(hashlib.sha256(username_trial).hexdigest()[3])
print(hashlib.sha256(username_trial).hexdigest()[6])
print(hashlib.sha256(username_trial).hexdigest()[2])
print(hashlib.sha256(username_trial).hexdigest()[7])
print(hashlib.sha256(username_trial).hexdigest()[1])
print(hashlib.sha256(username_trial).hexdigest()[8])
```
## Run 
. code 0 8 c 4 6 a a 4
. ` flag picoCTF{1n_7h3_kk3y_of_08c46aa4}
