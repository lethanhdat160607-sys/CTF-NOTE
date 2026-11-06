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

The server receives two integers, \(x\) and \(y\), and applies the following formula:
\[
s = w_1x + w_2y + b
\]
If \(s \ge 0\), the server returns "fires" (1). If \(s < 0\), the server returns "quiet" (0). The goal is to find the coefficients \(w_1\), \(w_2\), and \(b\) such that the formula's output matches the server's response for all pairs \((x, y)\) within the range \([-10, 10]\).
Analyzing the probes:
At \(y = 0\), the results show:
- \(x = 0, 1, 2 \rightarrow\) "quiet"
- \(x = 3, 4, 5, 10 \rightarrow\) "fires"
Thus, the threshold where the result changes lies between \(x = 2\) and \(x = 3\).

We also check the extremes of the range for \(y\):
- For \(x = 2\), both \(y = -10\) and \(y = 10\) result in "quiet".
- For \(x = 3\), both \(y = -10\) and \(y = 10\) result in "fires".
These results are consistent with a rule that does not depend on \(y\). A simple formula that fits is:
\[
s = x - 3
\]
In the format required by the problem:
\(w_1 = 1\)
\(w_2 = 0\)
\(b = -3\)
Verification:
- When \(x \le 2\), \(x - 3 < 0\), so the result is "quiet".
- When \(x \ge 3\), \(x - 3 \ge 0\), so the result is "fires".
- \(y\) has no effect because its coefficient is 0.
Therefore, send the command:
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

