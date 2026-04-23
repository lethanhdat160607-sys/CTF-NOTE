# 🚩Transformation - picoCTF 2021

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Easy
- **Target File:** `enc`
- **Key Skills And Tools:** python, hex, unicode, data encryption
---

## 🔍 Challenge 
I wonder what this really is...
enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])

### 🧪 Logic Extraction:

The challenge involved characters that looked like some kind of language. I used Cyberchef with the Magic tool to read them because this tool can read, analyze, decode, and apply many formulas. I set it to a mode that could decode many complex machine codes, which would increase my chances of success, and it flagged me.

<div align="center">
  <img width="1050" height="501" alt="image" src="https://github.com/user-attachments/assets/52b58a86-201c-496a-a580-67de1207f490" />
  <p> Cyberchef</p>
</div>

## 💻 The Solver (Python Script)

For the second solution, I used Python code for encoding because the challenge I encountered was a piece of code `enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])` which contains the `chr` and `ord` commands that encode characters and integers, and `>>8` which is probably a conversion to bit 8, and `& 0xFF)` is a comparison operation to retrieve information and read the file in `unicode` format. So I rewrote the code, ran it, and got the flag.
```
with open("enc", "r", encoding="utf-8") as f:
    encoded_content = f.read()

decoded = ""
for char in encoded_content:
    decoded += chr(ord(char) >> 8)
    decoded += chr(ord(char) & 0xFF)

print("flag", decoded)
```
#
My Python code is similar, but the coding method is different. I read the file first, then encode it using the `lstrip("0x")` function to remove the extra prefixes, resulting in a new code. I then use the `hex` function to encode it using the `decode()` command. It's similar to `utf-8` Unicode, the only difference being the use of commands to generate the flags.

```
>>> enc=open("enc").read()
>>> for c in enc:
...     print(hex(ord(c)).lstrip("0x"),end='')
...
7069636f4354467b31365f626974735f696e73743334645f6f665f385f62376636326361357d
>>>print(hex(ord(c)).lstrip
>>> print(bytes.fromhex("7069636f4354467b31365f626974735f696e73743334645f6f665f385f62376636326361357d").decode())
picoCTF{16_bits_inst34d_of_8_b7f62ca5}
```

## Run 
.flag picoCTF{16_bits_inst34d_of_8_b7f62ca5}.

