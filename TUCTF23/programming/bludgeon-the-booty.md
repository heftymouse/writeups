# Bludgeon The Booty

This challenge is a very simple 3-digit passcode lock, allowing us to increment or decrement a chosen digit.
```py
from pwn import *

io = remote('chal.tuctf.com', 30012)

for i in range(10):
    for j in range(10):
        for k in range(10):
            io.sendline(b'1')
            io.sendline(b'3')
            io.sendline(b'+')
        io.sendline(b'1')
        io.sendline(b'2')
        io.sendline(b'+')
    io.sendline(b'1')
    io.sendline(b'1')
    io.sendline(b'+')

io.interactive()
```
