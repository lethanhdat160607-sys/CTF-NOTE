<img width="1030" height="512" alt="image" src="https://github.com/user-attachments/assets/74e3d72d-ef35-4a0b-9990-387878ce9f3c" />


The problem provides a list of ASCII codes, and the hint suggests using the `chr` and `ord` functions to translate them. I used the `chr` function to translate the ASCII codes, and I wrote the two code snippets below to produce the flags.

```
arr = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]

result = ""
for x in arr:
    result += chr(x)
print(result)

result = "".join([chr(x) for x in arr])
print(result)
```

Run Python and get the flag.

```
┌──(venv)─(kali㉿kali)-[~/Tool/CTF]
└─$ python solve.py                                              
crypto{ASCII_pr1nt4bl3}
crypto{ASCII_pr1nt4bl3}

```
