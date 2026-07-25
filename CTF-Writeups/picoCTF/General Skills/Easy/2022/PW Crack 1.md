# 🚩 PW Crack 1 - picoCTF 2022

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `level1.flag.txt.enc`, `level1.py`
- **Key Skills And Tools:** python, reading file data
---

## 🔍 Challenge 

Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 in the same directory too.

### 🧪 Logic Extraction:

I used the `cat` command to read the Python code file.
```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat level1.py          
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################


flag_enc = open('level1.flag.txt.enc', 'rb').read()


def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_1_pw_check()


```

I rewrote the program to write down the password `user_pw = "691d"` correctly from the logic to check the file and call the XOR function to decrypt it: `decryption = str_xor(flag_enc.decode(), user_pw)` and print the result.
```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat solve.py 
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c, new_key_c) in zip(secret, new_key)])

# Load the encrypted flag bytes and decode to string
flag_enc = open('level1.flag.txt.enc', 'rb').read()

# The password checked in level_1_pw_check()
user_pw = "691d"

# Decrypt and print the flag
decryption = str_xor(flag_enc.decode(), user_pw)
print(decryption)

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ python3 solve.py                      
picoCTF{545h_r1ng1ng_56891419}

```

## Run

. flag picoCTF{545h_r1ng1ng_56891419}



