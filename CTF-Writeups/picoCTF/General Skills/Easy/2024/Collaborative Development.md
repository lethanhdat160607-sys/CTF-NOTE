# 🚩 binhexa - picoCTF 2024

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `nc titan.picoctf.net 56234`
- **Key Skills And Tools:** nc, genmin, reading data file
---

## 🔍 Challenge 

How well can you perfom basic binary operations?

Start searching for the flag here nc titan.picoctf.net 56234.

### 🧪 Logic Extraction:

I used Gemini to help with encoding and get results quickly.

<div align="center">
  <img width="816" height="553" alt="image" src="https://github.com/user-attachments/assets/63e5af27-5cca-4895-8086-695851962e6b" />


</div>

#
Binary operations (bitwise and arithmetic) used to solve CTF challenges:

& (AND): Returns 1 if both bits are 1.

| (OR): Returns 1 if at least one bit is 1.

<< (Left Shift): Shifts bits to the left, equivalent to doubling the number.

>> (Right Shift): Shifts bits to the right, equivalent to halving the number (rounding down).

+ / *: Adds and multiplies the values ​​of two binary numbers as with regular decimal numbers.
```

┌──(kali㉿kali)-[~/Tools/Misc]
└─$ nc titan.picoctf.net 56234

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 00000111
Binary Number 2: 00000110


Question 1/6:
Operation 1: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 00000110
Correct!

Question 2/6:
Operation 2: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 00000111
Correct!

Question 3/6:
Operation 3: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 00001110
Correct!

Question 4/6:
Operation 4: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 101010
Correct!

Question 5/6:
Operation 5: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1101
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00000011
Correct!

Enter the results of the last operation in hexadecimal: 0x3

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}
```

## Run

. flag picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}


