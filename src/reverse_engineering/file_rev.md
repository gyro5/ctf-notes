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