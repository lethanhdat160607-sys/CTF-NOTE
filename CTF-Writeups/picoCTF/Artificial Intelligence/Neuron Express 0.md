# 🚩 Neuron Express 0 - picoCTF 

- **Category:** Artificial Intelligence⚙️
- **Difficulty:** Easy
- **Target File:** `aureolin-pixie.cylabacademy.net 51264`
- **Key Skills And Tools:** pwn, python, Brute-force Space Search
---

## 🔍 Challenge 

Probe a 1D perceptron over the network. Send it integers and watch whether the neuron fires or not. Use those responses to figure out the underlying weight and bias, then submit your guess with the TEST command to earn the flag. Connect with netcat:

$ nc aureolin-pixie.cylabacademy.net 51264

The input bounds are shown on connect to keep the search small.
### 🧪 Logic Extraction:

```
from pwn import *

# Kết nối đến server
host = "aureolin-pixie.cylabacademy.net"
port = 51264

io = remote(host, port)

# Thu thập kết quả cho mọi x từ -10 đến 10
results = {}
for x in range(-10, 11):
    io.sendlineafter(b"x> ", str(x).encode())
    resp = io.recvline()
    # Nếu phản hồi chứa 'fires' thì output là 1, ngược lại 'quiet' là 0
    if b"fires" in resp:
        results[x] = 1
    else:
        results[x] = 0

print("Kết quả thu thập được:", results)

# Dò w và b trong khoảng nhỏ (ví dụ từ -10 đến 10)
found = False
for w in range(-10, 11):
    for b in range(-20, 21):
        match = True
        for x in range(-10, 11):
            # Quy tắc: w*x + b >= 0 -> 1, else 0
            expected = 1 if (w * x + b >= 0) else 0
            if expected != results[x]:
                match = False
                break
        if match:
            print(f"[+] Tìm thấy! w = {w}, b = {b}")
            # Gửi lệnh TEST
            io.sendlineafter(b"x> ", f"TEST {w} {b}".encode())
            print(io.recvall().decode())
            found = True
            break
    if found:
            break

io.close()
```

```
(venv) linuxdatkk@LAPTOP-C3MJQUU4:~/tool/file_ctf01$ python main.py
[*] Checking for new versions of pwntools
    To disable this functionality, set the contents of /home/linuxdatkk/.cache/.pwntools-cache-3.12/update to 'never' (old way).
    Or add the following lines to ~/.pwn.conf or ~/.config/pwn.conf (or /etc/pwn.conf system-wide):
        [update]
        interval=never
[*] You have the latest version of Pwntools (4.15.0)
[+] Opening connection to aureolin-pixie.cylabacademy.net on port 51264: Done
Kết quả thu thập được: {-10: 0, -9: 0, -8: 0, -7: 0, -6: 0, -5: 0, -4: 0, -3: 0, -2: 0, -1: 0, 0: 0, 1: 0, 2: 1, 3: 1, 4: 1, 5: 1, 6: 1, 7: 1, 8: 1, 9: 1, 10: 1}
[+] Tìm thấy! w = 1, b = -2
[+] Receiving all data: Done (64B)
[*] Closed connection to aureolin-pixie.cylabacademy.net port 51264
Perfect match! Here is your flag:
academy{n3ur0n_expr_7b1f1ea2}
```
## Run

. flag academy{n3ur0n_expr_7b1f1ea2}
