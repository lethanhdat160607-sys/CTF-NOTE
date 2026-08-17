# 🚩 FANTASY CTF - picoCTF 2025

- **Category:** General Skills⚙️
- **Difficulty:** Easy
- **Target File:** `fixme1.tar.gz`
- **Key Skills:** cargo, rust, tar, reading data code 

---

## 🔍 Challenge 

Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF.

Connect to the program with netcat:

$ nc verbal-sleep.picoctf.net 63660

### 🧪 Logic Extraction:
```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ tar xvfz fixme1.tar.gz
fixme1/
fixme1/Cargo.toml
fixme1/Cargo.lock
fixme1/src/
fixme1/src/main.rs
                     
```


```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat fixme1/src/main.rs
use xor_cryptor::XORCryptor;

fn main() {
    // Key for decryption
    let key = String::from("CSUCKS") // How do we end statements in Rust?

    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f", "5a", "60", "50", "11", "38", "1f", "3a", "60", "e9", "62", "20", "0c", "e6", "50", "d3", "35"];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        ret; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!(
        ":?", // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
} 
```


```
┌──(kali㉿kali)-[~/Tools/Misc/fixme1/src]
└─$ cat main.rs 
use xor_cryptor::XORCryptor;

fn main() {
    // Key for decryption
    let key = String::from("CSUCKS"); // How do we end statements in Rust?

    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f", "5a", "60", "50", "11", "38", "1f", "3a", "60", "e9", "62", "20", "0c", "e6", "50", "d3", "35"];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!(
        "{}", // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
}

```

```
┌──(kali㉿kali)-[~/Tools/Misc/fixme1/src]
└─$ cargo run    
    Updating crates.io index
  Downloaded crossbeam-deque v0.8.5
  Downloaded xor_cryptor v1.2.3
  Downloaded crossbeam-epoch v0.9.18
  Downloaded rayon-core v1.12.1
  Downloaded crossbeam-utils v0.8.20
  Downloaded either v1.13.0
  Downloaded rayon v1.10.0
  Downloaded 7 crates (379.2KiB) in 1.23s
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/kali/Tools/Misc/fixme1)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 20.28s
     Running `/home/kali/Tools/Misc/fixme1/target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}

```


## Run 
.flag picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}

