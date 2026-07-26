# 🚩 vault-door-1 - picoCTF 2019

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium
- **Target File:** `VaultDoor1.java`
- **Key Skills And Tool:** cat, java, code comprehension

---

## 🔍 Challenge 

This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: VaultDoor1.java



### 🧪 Logic Extraction:

I used the `cat` command to extract data from a file and I found keys inside that I suspect are flag keys.
```

    public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '8' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == '9' &&
               password.charAt(30) == 'd' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == 'e' &&
               password.charAt(26) == '2' &&
               password.charAt(31) == '8';
    
```

Use Notepad++ to sort and search easily because the key is already in the code; we can combine them to get the flag.

<div align="center">
  <img width="823" height="692" alt="image" src="https://github.com/user-attachments/assets/3f023c9d-9b37-4769-8bbf-18cb28b6932b" />


</div>




## Run 
.flag picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_29e8d8}
