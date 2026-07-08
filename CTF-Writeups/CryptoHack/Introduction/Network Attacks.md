<img width="1027" height="663" alt="image" src="https://github.com/user-attachments/assets/df95b3eb-2fe2-48b9-95e6-42f6f5c6f80d" />

#

I downloaded the pwntools library using `pip install pwntools`and also created a virtual environment using `sudo apt install python3.13-venv`,We create a virtual machine using the command `python3 -m venv venv`, access the virtual machine using the command `source venv/bin/activate`, and exit the virtual machine using the command `deactivate`.


<div align="center">
  <img width="449" height="576" alt="image" src="https://github.com/user-attachments/assets/bb835892-f714-4234-9895-8208f69053f8" />
</div>

#

In summary, the code above connects to the server, reads the first four lines of data from the server, creates a dictionary named `{"buy": "clothes"}` (this is the part we need to focus on), sends this dictionary code back to the server as JSON, reads the response from the server, decodes the JSON, and prints the result to the screen.

According to the code logic, when you send `{"buy": "clothes"}`, its value is `buy`. If it's `clothes`, it returns either the purchase information or a message indicating that it has been purchased. When you change it to `{"buy": "flag"}`, the server will run a conditional statement, usually an `if/else` or a switch statement. If the `buy` key has a flag value, it returns the flag content.

```
request = {
    "buy": "flag"
}
```



Running Python will give you the flag.

```
┌──(venv)─(kali㉿kali)-[~/Tool]
└─$ python pwntools_example_72a60ff13df200692898bb14a316ee0b.py
[+] Opening connection to socket.cryptohack.org on port 11112: Done
b"Welcome to netcat's flag shop!\n"
b'What would you like to buy?\n'
b"I only speak JSON, I hope that's ok.\n"
b'\n'
{'flag': 'crypto{sh0pp1ng_f0r_fl4g5}'}
[*] Closed connection to socket.cryptohack.org port 11112

```
