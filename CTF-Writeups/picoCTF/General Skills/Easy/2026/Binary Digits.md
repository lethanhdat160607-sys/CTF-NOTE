# 🚩Binary Digits - picoCTF 

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `digits.bin`
- **Key Skills And Tools:**  binary, render image, Entropy analysis, Byte mapping, Pattern recognition 

## 🔍 Challenge 

This file doesn't look like much... just a bunch of 1s and 0s. But maybe it's not just random noise. Can you recover anything meaningful from this?
Download the file here.

### 🧪 Logic Extraction:

When I opened the file, I saw a lot of binary code; it looked like an image. 

<div align="center">

  <img width="1365" height="608" alt="image" src="https://github.com/user-attachments/assets/758ad25f-5269-42e5-8381-c54a1f180eda" />

</div>


#
We can use Cyberchef to convert the binary code, and it has a mode to convert it to an image and then to a flag.

<div align="center">
  <img width="1057" height="529" alt="image" src="https://github.com/user-attachments/assets/61155e1c-0021-4af1-b6be-550ef92228fe" />
  <p> Cyberchef </p>
<div>


## Run 
.flag picoCTF{h1dd3n_1n_th3_b1n4ry_d4e39e9e}
