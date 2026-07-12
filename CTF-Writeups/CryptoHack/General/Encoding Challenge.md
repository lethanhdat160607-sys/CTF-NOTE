<img width="1053" height="584" alt="image" src="https://github.com/user-attachments/assets/4baa4424-7c33-4900-8915-0ec9b0a2d256" />


This code operates as a server-side interaction where the server acts as a game master, continuously sending you data in JSON format. Each time the server sends data, it randomly selects one of five encodings (base64, hex, rot13, bigint, utf-8). The authentication mechanism is that the client must correctly analyze the encoding type, decode the encoded content back into plain text, and send it back to the server in JSON. If correct, the server allows it to proceed to the next step. This process is limited to 100 attempts.

```
#!/usr/bin/env python3

from Crypto.Util.number import bytes_to_long, long_to_bytes
from utils import listener # this is cryptohack's server-side module and not part of python
import base64
import codecs
import random

FLAG = "crypto{????????????????????}"
ENCODINGS = [
    "base64",
    "hex",
    "rot13",
    "bigint",
    "utf-8",
]
with open('/usr/share/dict/words') as f:
    WORDS = [line.strip().replace("'", "") for line in f.readlines()]


class Challenge():
    def __init__(self):
        self.no_prompt = True # Immediately send data from the server without waiting for user input
        self.challenge_words = ""
        self.stage = 0

    def create_level(self):
        self.stage += 1
        self.challenge_words = "_".join(random.choices(WORDS, k=3))
        encoding = random.choice(ENCODINGS)

        if encoding == "base64":
            encoded = base64.b64encode(self.challenge_words.encode()).decode() # wow so encode
        elif encoding == "hex":
            encoded = self.challenge_words.encode().hex()
        elif encoding == "rot13":
            encoded = codecs.encode(self.challenge_words, 'rot_13')
        elif encoding == "bigint":
            encoded = hex(bytes_to_long(self.challenge_words.encode()))
        elif encoding == "utf-8":
            encoded = [ord(b) for b in self.challenge_words]

        return {"type": encoding, "encoded": encoded}

    #
    # This challenge function is called on your input, which must be JSON
    # encoded
    #
    def challenge(self, your_input):
        if self.stage == 0:
            return self.create_level()
        elif self.stage == 100:
            self.exit = True
            return {"flag": FLAG}

        if self.challenge_words == your_input["decoded"]:
            return self.create_level()

        return {"error": "Decoding fail"}


import builtins; builtins.Challenge = Challenge # hack to enable challenge to be run locally, see https://cryptohack.org/faq/#listener
listener.start_server(port=13377)

```

```
FLAG = "crypto{????????????????????}"
ENCODINGS = [
    "base64",
    "hex",
    "rot13",
    "bigint",
    "utf-8",
]
```

```
 def create_level(self):
        self.stage += 1
        self.challenge_words = "_".join(random.choices(WORDS, k=3))
        encoding = random.choice(ENCODINGS)

        if encoding == "base64":
            encoded = base64.b64encode(self.challenge_words.encode()).decode() # wow so encode
        elif encoding == "hex":
            encoded = self.challenge_words.encode().hex()
        elif encoding == "rot13":
            encoded = codecs.encode(self.challenge_words, 'rot_13')
        elif encoding == "bigint":
            encoded = hex(bytes_to_long(self.challenge_words.encode()))
        elif encoding == "utf-8":
            encoded = [ord(b) for b in self.challenge_words]

        return {"type": encoding, "encoded": encoded}
```

# Code 
```
from pwn import *
import json
import base64
import codecs
from Crypto.Util.number import long_to_bytes

# Establish connection to the server
server = remote('socket.cryptohack.org', 13377)

def receive_json():
    line = server.recvline()
    return json.loads(line.decode())

def send_json(data):
    server.sendline(json.dumps(data).encode())

# Loop 100 times to solve each challenge stage
for i in range(101):
    received_data = receive_json()
    
    # Check if the flag has been received
    if "flag" in received_data:
        print(f"\nSUCCESS! Flag: {received_data['flag']}")
        break
        
    print(f"Round {i}: Encoding type = {received_data['type']}")
    
    encoding_type = received_data["type"]
    encoded_value = received_data["encoded"]
    
    # Decoding logic based on the encoding type
    if encoding_type == "base64":
        decoded_value = base64.b64decode(encoded_value).decode()
    elif encoding_type == "hex":
        decoded_value = bytes.fromhex(encoded_value).decode()
    elif encoding_type == "rot13":
        decoded_value = codecs.decode(encoded_value, 'rot_13')
    elif encoding_type == "bigint":
        decoded_value = long_to_bytes(int(encoded_value, 16)).decode()
    elif encoding_type == "utf-8":
        decoded_value = "".join([chr(byte) for byte in encoded_value])
        
    print(f"Decoded value: {decoded_value}")
    
    # Send the decoded answer back to the server
    send_json({"decoded": decoded_value})

```  
