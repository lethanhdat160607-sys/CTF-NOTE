# 🚩 keygenme-py - picoCTF 2021

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium 🟠
- **Target File:** `keygenme-trial.py`
- **Key Skills:** Static Analysis, Python Scripting, SHA256 Hashing

---

## 🔍 1. Challenge Overview
In this challenge, we are given a Python script called `keygenme-trial.py`. The script acts as a trial version of an "Arcane Calculator." To unlock the full version and reveal the flag, we must enter a valid **License Key**.

### 📋 Initial Observations
By reading the source code, I identified the key structure:
- `username_trial = "BENNETT"`
- `key_part_static1_trial = "picoCTF{1n_7h3_kk3y_of_"`
- `key_part_dynamic1_trial = "xxxxxxxx"` (8 missing characters)
- `key_part_static2_trial = "}"`

---

## 🛠️ 2. Static Analysis & Reverse Engineering
The core logic resides in the `check_key(key, username_trial)` function. 

The script validates the 8 dynamic characters by comparing our input with specific indices of the **SHA256 hash** of the username `"BENNETT"`.

### 🧪 Logic Extraction:
I traced the `if` statements and found the required order of hash characters:
1. `key[i] == hash[4]`
2. `key[i+1] == hash[5]`
3. `key[i+2] == hash[3]`
4. `key[i+3] == hash[6]`
5. `key[i+4] == hash[2]`
6. `key[i+5] == hash[7]`
7. `key[i+6] == hash[1]`
8. `key[i+7] == hash[8]`

---

## 💻 3. The Solver (Python Script)
Instead of manual calculation, I wrote a small automation script to generate the dynamic part:

```python
import hashlib

# 1. Target Data
username = b"BENNETT"
prefix = "picoCTF{1n_7h3_kk3y_of_"
suffix = "}"

# 2. Generate SHA256
digest = hashlib.sha256(username).hexdigest()

# 3. Extract characters based on the logic: 4, 5, 3, 6, 2, 7, 1, 8
order = [4, 5, 3, 6, 2, 7, 1, 8]
dynamic_part = "".join([digest[i] for i in order])

# 4. Result
print(f"Full Flag: {prefix}{dynamic_part}{suffix}")
