# 🚩 PW Crack 2 - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `level2.flag.txt.enc`, `level2.py`
- **Key Skills And Tools:** python, 
---

## 🔍 Challenge 

Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 in the same directory too.

### 🧪 Logic Extraction:

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat level2.py
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

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()

```

```

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat solve.py
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()



user_pw = chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)

decryption = str_xor(flag_enc.decode(), user_pw)


print(decryption)
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ python3 solve.py 
picoCTF{tr45h_51ng1ng_489dea9a}

```

## Run

. flag picoCTF{545h_r1ng1ng_56891419}




