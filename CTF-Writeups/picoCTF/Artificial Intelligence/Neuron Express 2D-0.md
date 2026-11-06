# 🚩 Neuron Express 2D-0 - picoCTF 

- **Category:** Artificial Intelligence⚙️
- **Difficulty:** Easy
- **Target File:** `└─$ nc xebec.cylabacademy.net 11663`
- **Key Skills And Tools:** 
---

## 🔍 Challenge 

Probe a 2D perceptron over the network. Send it integer pairs (x, y) and watch whether the neuron fires or not. Use those responses to figure out the underlying integer weights and bias, then submit your guess with the TEST command to earn the flag. Connect with netcat:

$ nc xebec.cylabacademy.net 11663


### 🧪 Solution

Máy chủ nhận hai số nguyên x và y, rồi áp dụng một công thức:
\[
s = w_1x + w_2y + b
\]
Nếu \(s \ge 0\), máy chủ trả fires (1). Nếu \(s < 0\), máy chủ trả quiet (0). Cần tìm bộ hệ số w1, w2, b sao cho kết quả của công thức khớp với máy chủ trên mọi cặp (x,y) trong phạm vi [-10,10].
Phân tích các probe
Ở y=0, các kết quả cho thấy:
- x=0, 1, 2 → quiet
- x=3, 4, 5, 10 → fires
Vậy ngưỡng đổi kết quả nằm giữa x=2 và x=3.

Ta còn kiểm tra ở hai đầu phạm vi y:
- x=2 với y=-10 và y=10 đều quiet
- x=3 với y=-10 và y=10 đều fires
Các kết quả phù hợp với quy tắc không phụ thuộc vào y. Một công thức đơn giản khớp là:
\[
s = x - 3
\]
Viết theo dạng của đề:
w1 = 1
w2 = 0
b  = -3
Kiểm tra
- Khi x ≤ 2, \(x-3 < 0\), nên kết quả là quiet.
- Khi x ≥ 3, \(x-3 \ge 0\), nên kết quả là fires.
- y không ảnh hưởng vì hệ số của y là 0.
Do đó gửi lệnh:
TEST 1 0 -3

```
┌──(kali㉿kali)-[~/Tool_hacker/CTF]
└─$ nc xebec.cylabacademy.net 11663
Welcome to Neuron Express 2D-0!
Probe the 2D perceptron, then submit its weights and bias.
Send two integers (x, y) within the bounds to see if the perceptron fires (1) or stays quiet (0).
- Bounds: [-10, 10] for both x and y
- Output rule: w1*x + w2*y + b >= 0 -> 1, else 0.
- Weights and bias are integers.
- Default command: submit x and y to see whether the perceptron activates.
- Format: x,y or x y (comma or space separated)
- Command: TEST w1 w2 b to submit integer weights and bias.
- The guess must match outputs for every integer (x, y) in range.

Type HELP for a reminder or EXIT to quit.

[1/128] (x,y)> 0 0
Perceptron stays quiet.
[2/128] (x,y)> 10 0 
Perceptron fires!
[3/128] (x,y)> 5 0
Perceptron fires!
[4/128] (x,y)> 1 0
Perceptron stays quiet.
[5/128] (x,y)> 2 0
Perceptron stays quiet.
[6/128] (x,y)> 4 0
Perceptron fires!
[7/128] (x,y)> 3 0
Perceptron fires!
[8/128] (x,y)> 2 -10
Perceptron stays quiet.
[9/128] (x,y)> 2 10
Perceptron stays quiet.
[10/128] (x,y)> 3 -10
Perceptron fires!
[11/128] (x,y)> 3 10
Perceptron fires!
[12/128] (x,y)> 1 0 -3
Expected two integers (x, y). Try again.
[13/128] (x,y)> TEST 1 0 -3
Perfect match! Here is your flag:

```

## RUN
flag. academy{n3ur0n_expr_2d_a59ea424}

