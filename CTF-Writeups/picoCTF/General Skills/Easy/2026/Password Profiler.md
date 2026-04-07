# 🚩 keygenme-py - picoCTF 2021

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium 
- **Target File:** `keygenme-trial.py`
- **Key Skills:** Static Analysis, Python Scripting, SHA256 Hashing

---

## 🔍 Challenge 
In this challenge, we are provided with a Python script called `keygenme-trial.py`. It acts as a trial version of an "Arcane Calculator." To 

### 📋 Core Script Highlights


## 🛠️ Static Analysis & Reverse Engineering


### 🧪 Logic Extraction:
By tracing the `if` statements in the code, I identified the exact indices required from the hex-digest of the hash:


. ` flag picoCTF{1n_7h3_kk3y_of_08c46aa4}
