# File Reverse Engineering

## Tools

- **Pickle files**: Python has built-in `pickletools` library to work with `pickle`/`pkl` file (serialised Python object).

    Example:
    ```python
    import pickletools as pk

    # This will print the disassembly of the file in Pickle's assembly format
    with open("a.pkl", "rb") as f:
        pk.dis(f)
    ```

## Binary files provided as bitstring

Binary files can be provided as a bitstring or hexstring. This can be converted to an actual file using the Python `bitstring` library.

Example:

```python
import bitstring as bs

# Multiple options
a = bs.BitArray(bin='0011100110010')
a = bs.BitArray(hex='7ab3cd')
a = bs.BitArray('0x123')
a = bs.BitArray('0b1001')

# Get alternative representations
a.bin
a.hex
a.oct

# Write to file
open('myfile', 'wb').write(a.tobytes())
```

See <https://bitstring.readthedocs.io/en/stable/interpretation.html> for documentation.