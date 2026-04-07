# 🚩 ping-cmd - picoCTF 2026

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Link:** `nc mysterious-sea.picoctf.net 64791`
- **Key Skills:**  
---

## 🔍 Challenge 
Can you make the server reveal its secrets? It seems to be able to ping Google DNS, but what happens if you get a little creative with your input?
You can connect to the service here `nc mysterious-sea.picoctf.net 64791`

### 🧪 Logic Extraction:
- strings: Filters out binary "junk," keeping only readable characters.
- Uses: Searches for hidden text, error messages, function names, or URLs in non-text files (such as .exe, .bin, .png images, etc.).
- | (Pipe): The funnel. Pushes results from the previous command to the next.
- grep: The crawler. Only picks out lines containing the keyword you want.
```
~ strings file
~ strings strings | grep pico
```
## Run 
.flag picoCTF{5tRIng5_1T_60eA8fdA}
