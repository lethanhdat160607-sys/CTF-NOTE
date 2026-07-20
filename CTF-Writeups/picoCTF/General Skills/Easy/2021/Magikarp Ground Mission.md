# 🚩 Magikarp Ground Mission - picoCTF 2019

- **Category:** General Skills ⚙️
- **Difficulty:** Easy
- **Target File:** ` ctf-player@wily-courier.picoctf.net`
- **Key Skills And Tools:** ssh, sshpass, 
---

## 🔍 Challenge 

Do you know how to move between directories and read files in the shell? Start the container, ssh to it, and then ls once connected to begin.

Login via ssh as ctf-player with the password, 8c606eb1 on the host wily-courier.picoctf.net and port 63898.

### 🧪 Logic Extraction:


```                                                       

sshpass -p "8c606eb1" ssh ctf-player@wily-courier.picoctf.net -p 63898

```

```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt

ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_

```

```
ctf-player@pico-chall$ ls /
2of3.flag.txt  bin  boot  challenge  dev  etc  home  instructions-to-3of3.txt  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

ctf-player@pico-chall$ cat /2of3.flag.txt
0ut_0f_//4t3r_
```

```
ctf-player@pico-chall$ ls ~
3of3.flag.txt  drop-in

ctf-player@pico-chall$ cat ~/3of3.flag.txt
0b24fc4f}
```

  

## Run

. flag picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}

