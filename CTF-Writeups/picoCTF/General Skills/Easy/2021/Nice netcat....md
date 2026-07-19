# 🚩 Nice netcat.... - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** `nc wily-courier.picoctf.net 58819`
- **Key Skills And Tools:** nc, connect to server
---

## 🔍 Challenge 

There is a nice program that you can talk to by using this command in a shell:

$ nc wily-courier.picoctf.net 58819, but it doesn't speak English...

### 🧪 Logic Extraction:

We run the `nc` command to get the decimal code.

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$  nc wily-courier.picoctf.net 
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
102 
55 
97 
54 
101 
125 
10 
```

I used a ready-made online tool to convert decimal codes to ASCII codes.

<div align="center">
  <img width="1365" height="655" alt="image" src="https://github.com/user-attachments/assets/321ae04f-950e-4d3d-a527-66a363a4f41d" />
</div>

## Run

. flag picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}

