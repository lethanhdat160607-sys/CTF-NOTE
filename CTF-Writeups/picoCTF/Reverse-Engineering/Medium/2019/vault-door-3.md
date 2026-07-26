# 🚩 vault-door-3 - picoCTF 2019

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium
- **Target File:** `VaultDoor3.java`
- **Key Skills And Tool:** cat, java, python, code comprehension

---

## 🔍 Challenge 

This vault uses for-loops and byte arrays.

The source code for this vault is here: VaultDoor3.java


### 🧪 Logic Extraction:

I used the `cat` command to extract data and saw a flag appear inside, but when I tried to send it, it didn't work. After reviewing the code logic, I discovered that the `for` conditions I used were running a loop to iterate through the code and extract the flags, and we need to reverse the conversion.
```
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm1cg04e_u_4_m6rb42");

```

## 💻 The Solver (Python Script)

``` python
#!/usr/bin/python

password = list("--------------------------------")
buffer = "jU5t_a_sna_3lpm1cg04e_u_4_m6rb42"

for i in range(0, 8):
    password[i] = buffer[i]

for i in range(8, 16):
    password[23-i] = buffer[i]

for i in range(16, 32, 2):
    password[46-i] = buffer[i]

for i in range(31, 16, -2):
    password[i] = buffer[i]

flag = ''.join(password)
print(f"Flag: picoCTF{{{flag}}}")
```

## Run

.flag picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_e60bc2}
