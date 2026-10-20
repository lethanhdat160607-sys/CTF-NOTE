<img width="1585" height="468" alt="image" src="https://github.com/user-attachments/assets/75084841-d5ae-44ec-a88a-c33eee7991e9" />



```
text: 0e 0b 21 3f 26 04 1e 48 0b 26 21 7f 27 34 2e 17 5d 0e 07 0a 3c 5b 10 3e 25 26 21 7f 27 34 2e 17 5d 0e 07 7e 26 34 51 15 01 04
```

```
key: c r y p t o {
ascii hex: 63  72  79  70  74  6f  7b
```

```
0e XOR 63 = 6d = 'm'
0b XOR 72 = 79 = 'y'
21 XOR 79 = 58 = 'X'
3f XOR 70 = 4f = 'O'
26 XOR 74 = 52 = 'R'
04 XOR 6f = 6b = 'k'
1e XOR 7b = 65 = 'e'

keyflag: myXORke 
```

Run Python and get the flag.


```
┌──(venv)─(kali㉿kali)-[~/Cybersecurity_Hub/07_Cryptography]
└─$ cat solve_xor_you_dont.py
ciphertext = bytes.fromhex(
    "0e0b213f26041e480b26217f27342e175d0e070a3c5b103e"
    "2526217f27342e175d0e077e263451150104"
)
key = b"myXORkey"

plaintext = bytes(
    byte ^ key[i % len(key)]
    for i, byte in enumerate(ciphertext)
)

print(plaintext.decode())

```
