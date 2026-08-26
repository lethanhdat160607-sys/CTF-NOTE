# 🚩 Rust fixme 2 - picoCTF 2025

- **Category:** General Skills⚙️
- **Difficulty:** Easy
- **Target File:** `fixme2.tar.gz`
- **Key Skills:** cargo, rust, tar, reading data code 

---

## 🔍 Challenge 

The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?

Download the Rust code here
.

### 🧪 Logic Extraction:
I used the `tar xvfz` command: `x` extracts files from the archive, `v` displays the list of files being extracted on the screen, `f` specifies the source archive file (fixme1.tar.gz), and `z` decompresses the gzip format.


```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ tar xvfz fixme2.tar.gz
fixme2/
fixme2/Cargo.toml
fixme2/Cargo.lock
fixme2/src/
fixme2/src/main.rs

```
I used the `cat` command to display the code file and noticed that the code contains errors.


```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat fixme2/src/main.rs
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &String){ // How do we pass values to a function that we want to change?

    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    println!("{}", borrowed_string);
}


fn main() {
    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "0d", "c4", "60", "f2", "12", "a0", "18", "03", "51", "03", "36", "05", "0e", "f9", "42", "5b"];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    let party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
}   
```
I've fixed the code.

```
┌──(kali㉿kali)-[~/Tools/Misc]
└─$ cat fixme2/src/main.rs
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?

    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    println!("{}", borrowed_string);
}


fn main() {
    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "0d", "c4", "60", "f2", "12", "a0", "18", "03", "51", "03", "36", "05", "0e", "f9", "42", "5b"];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    let mut party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &mut party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
}

```
I used the `cargo run` command to compile and check the source code, compiling the src/main.rs file and its dependencies into a binary executable file. If the source code changes, it executes immediately, so the compilation automatically runs the file without needing to be manually called like the `rustc` command.


```
┌──(kali㉿kali)-[~/Tools/Misc/fixme2]
└─$ cargo run
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/kali/Tools/Misc/fixme2)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 23.03s
     Running `target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}

```
## Run 
.flag picoCTF{4r3_y0u_h4v1n5_fun_y31?}
