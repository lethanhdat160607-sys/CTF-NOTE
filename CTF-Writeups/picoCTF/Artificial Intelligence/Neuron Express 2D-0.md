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
### 🧪 Solution
I wrote this Python code to extract flags from the server.


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

