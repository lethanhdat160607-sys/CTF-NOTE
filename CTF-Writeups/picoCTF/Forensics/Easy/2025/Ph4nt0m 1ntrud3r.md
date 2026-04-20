# 🚩Ph4nt0m 1ntrud3r - picoCTF 2025

- **Category:** Forensics ⚙️
- **Difficulty:** Easy
- **Target File:** `pcap file`
- **Key Skills And Tools:** Aircrack-ng, Wireshark ,Password cracking and decryption
---

## 🔍 Challenge 

A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.
To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!
Find the PCAP file here Network Traffic PCAP file and try to get the flag.


### 🧪 Logic Extraction:


<div align="center">

</div> 



```
Frame 2: bnRfdGg0dA==
Frame 3 : fQ==
Frame 5: ZTFmZjA2Mw==
Frame 9: XzM0c3lfdA==
Frame 10: ezF0X3c0cw==
Frame 12: cGljb0NURg==
Frame 21: YmhfNHJfMg==
```

## Code Python 

```
import itertools

def generate_pico_flags(data_list):
    """
    Generates all permutations and formats them as picoCTF{}
    """
    # Create all possible permutations of the input list
    permutations = list(itertools.permutations(data_list))
    
    flag_list = []
    for p in permutations:
        # Join segments into the variable part
        variable_content = "".join(map(str, p))
        
        # Correct f-string syntax:
        # picoCTF{1t_w4s -> Fixed prefix
        # {variable_content} -> The moving parts
        # } -> Closing bracket
        full_flag = f"picoCTF{{1t_w4s{variable_content}}}" # f"picoCTF{{key{ble_content}}}"
        
        flag_list.append(full_flag)
    
    return flag_list

# Your input data segments
input_data = ["nt_th4t", "e1ff063", "_34sy_t", "bh_4r_2"]

# Execute generation
results = generate_pico_flags(input_data)

# Print results to console
print(f"--- Total Flags Generated: {len(results)} ---")
for index, flag in enumerate(results, 1):
    print(f"{index}: {flag}")

# Export to file
filename = "flags_wordlist.txt"
try:
    with open(filename, "w") as f:
        for flag in results:
            f.write(flag + "\n")
    print(f"\n[!] Success: Saved to '{filename}'")
except IOError as e:
    print(f"\n[!] Error saving file: {e}")
```

```
1: picoCTF{1t_w4snt_th4te1ff063_34sy_tbh_4r_2}
2: picoCTF{1t_w4snt_th4te1ff063bh_4r_2_34sy_t}
3: picoCTF{1t_w4snt_th4t_34sy_te1ff063bh_4r_2}
4: picoCTF{1t_w4snt_th4t_34sy_tbh_4r_2e1ff063}
5: picoCTF{1t_w4snt_th4tbh_4r_2e1ff063_34sy_t}
6: picoCTF{1t_w4snt_th4tbh_4r_2_34sy_te1ff063}
7: picoCTF{1t_w4se1ff063nt_th4t_34sy_tbh_4r_2}
8: picoCTF{1t_w4se1ff063nt_th4tbh_4r_2_34sy_t}
9: picoCTF{1t_w4se1ff063_34sy_tnt_th4tbh_4r_2}
10: picoCTF{1t_w4se1ff063_34sy_tbh_4r_2nt_th4t}
11: picoCTF{1t_w4se1ff063bh_4r_2nt_th4t_34sy_t}
12: picoCTF{1t_w4se1ff063bh_4r_2_34sy_tnt_th4t}
13: picoCTF{1t_w4s_34sy_tnt_th4te1ff063bh_4r_2}
14: picoCTF{1t_w4s_34sy_tnt_th4tbh_4r_2e1ff063}
15: picoCTF{1t_w4s_34sy_te1ff063nt_th4tbh_4r_2}
16: picoCTF{1t_w4s_34sy_te1ff063bh_4r_2nt_th4t}
17: picoCTF{1t_w4s_34sy_tbh_4r_2nt_th4te1ff063}
18: picoCTF{1t_w4s_34sy_tbh_4r_2e1ff063nt_th4t}
19: picoCTF{1t_w4sbh_4r_2nt_th4te1ff063_34sy_t}
20: picoCTF{1t_w4sbh_4r_2nt_th4t_34sy_te1ff063}
21: picoCTF{1t_w4sbh_4r_2e1ff063nt_th4t_34sy_t}
22: picoCTF{1t_w4sbh_4r_2e1ff063_34sy_tnt_th4t}
23: picoCTF{1t_w4sbh_4r_2_34sy_tnt_th4te1ff063}
24: picoCTF{1t_w4sbh_4r_2_34sy_te1ff063nt_th4t}
```
## Run 
.flag picoCTF{1t_w4snt_th4t_34sy_tbh_4r_2e1ff063}
