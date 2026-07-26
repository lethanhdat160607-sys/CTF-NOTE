# 🚩 vault-door-4 - picoCTF 2019

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium
- **Target File:** `VaultDoor4.java`
- **Key Skills And Tool:** cat, java, python, code comprehension

---

## 🔍 Challenge 

This vault uses ASCII encoding for the password.

The source code for this vault is here: VaultDoor4.java

### 🧪 Logic Extraction:

```
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
        String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
        if (vaultDoor.checkPassword(input)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 067 , 065 ,
            '9' , '6' , '0' , '0' , 'a' , 'b' , 'c' , '3' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}
```


## 💻 The Solver (Python Script)

``` python
myBytes = [
    106, 85, 53, 116, 95, 52, 95, 98,
    0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
    0o142, 0o131, 0o164, 0o63, 0o163, 0o137, 0o67, 0o65,
    ord('9'), ord('6'), ord('0'), ord('0'), ord('a'), ord('b'), ord('c'), ord('3')
]

password = "".join(chr(b) for b in myBytes)
print(f"picoCTF{{{password}}}")
```

## Run

.flag picoCTF{jU5t_4_bUnCh_0f_bYt3s_759600abc3}
