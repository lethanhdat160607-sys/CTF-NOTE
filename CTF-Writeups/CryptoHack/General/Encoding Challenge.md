<img width="1053" height="584" alt="image" src="https://github.com/user-attachments/assets/4baa4424-7c33-4900-8915-0ec9b0a2d256" />


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
