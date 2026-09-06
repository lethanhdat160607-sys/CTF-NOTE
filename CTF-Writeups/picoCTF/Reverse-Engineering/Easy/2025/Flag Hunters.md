# 🚩 Flag Hunters- picoCTF 2025

- **Category:** Reverse Engineering ⚙️
- **Difficulty:** Medium 
- **Target File:** `lyric-reader.py`, `nc verbal-sleep.picoctf.net 63231`
- **Key Skills And Tool:** python, data mining

---

## 🔍 Challenge 

Lyrics jump from verses to the refrain kind of like a subroutine call. There's a hidden refrain this program doesn't print by default. Can you get it to print it? There might be something in it for you.
The program's source code can be downloaded here.
Connect to the program with netcat:
`$ nc verbal-sleep.picoctf.net 63231`



### 🧪 Solution
This challenge involves accessing a server with a Python code file that we need to exploit. The part I paid the most attention to was the `while` loop; I suspect the error lies there.

```
 while not finished and line_count < MAX_LINES:
    line_count += 1
    for line in song_lines[lip].split(';'):
      if line == '' and song_lines[lip] != '':
        continue
      if line == 'REFRAIN':
        song_lines[refrain_return] = 'RETURN ' + str(lip + 1)
        lip = refrain
      elif re.match(r"CROWD.*", line):
        crowd = input('Crowd: ')
        song_lines[lip] = 'Crowd: ' + crowd
        lip += 1
      elif re.match(r"RETURN [0-9]+", line):
        lip = int(line.split()[1])
      elif line == 'END':
        finished = True
      else:
        print(line, flush=True)
        time.sleep(0.5)
        lip += 1
```

This code allows the user to input data that changes the system's structure. The code `song_lines[lip] = 'Crowd: ' + crowd ` can overwrite and move the cursor to the next section, back to `song_lines[lip]`. What if I use a special character like `RETURN` to exploit it, causing it to return a flag? 

```
elif re.match(r"CROWD.*", line):
        crowd = input('Crowd: ')
        song_lines[lip] = 'Crowd: ' + crowd
        lip += 1
 elif re.match(r"RETURN [0-9]+", line):
        lip = int(line.split()[1])
```

So I entered `; RETURN` and it worked perfectly, and the navigation and flag were displayed.Why? Because in this loop it says `for line in song_lines[lip].split(';'):`
This is because our input data is manipulated and reads line by line, but when we use `;` we can read multiple lines, and then with the data input mechanism, the system changes as described above

<div align="center"> 
  <img width="550" height="387" alt="image" src="https://github.com/user-attachments/assets/6c8667e3-20f6-4a9e-8696-a74ee19ded47" />

</div>

## Run 
. ` flag picoCTF{70637h3r_f0r3v3r_c373964d}
