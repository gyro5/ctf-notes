# Steganography

Based on the checklist on <https://georgeom.net/StegOnline/checklist>, with some additional notes and tools. For all tools, use `tldr` (from tealdeer package) for quick help.

## 1. Basic checks

Basic initial checks:

- `file` command: Check file type.

- `exiftool`: Check metadata for any information, geolocations, comment strings, etc.

- `strings`: View all embedded strings in the file.

    Use `strings -n 7 -t x filename.png` for more information (`-n 7` for strings of length 7+, `-t x` to show positions of strings).

## 2. Check for embedded files

Tools to check for embedded files in a challenge file:

- `binwalk`: Check for embedded files.
    + `binwalk file.png`: Scan the file for embedded files.
    + `binwalk -e file.png`: Extract embedded files.
    + `binwalk -D '.*' file.png`: Force extract all types of embedded files.

- `foremost`: Alternative to `binwalk`.

- `steghide`: Scan for hidden files. __Commonly used when there is a password.__
    + `steghide extract -sf file.png`: Extract hidden files.
    + `steghide info file.png`: Display file information and try to detect hidden files.
    + `stegseek` is a program that uses brute force to crack `steghide` password.

- Other tool for password-protected data:
    + [OpenStego](https://www.openstego.com/)
    + [Stegpy](https://github.com/Baldanos/Stegpy)
    + [Outguess](https://outguess.rbcafe.com/)

## 3. General steganography tools

General steganography tools that should be tried:

- `stegsnow`: For whitespace steganography on text files.

- [`zsteg`](https://github.com/zed-0xff/zsteg): Steganography tool that can perform many types of extraction. Installed with Ruby Gem (`gem install zsteg`).

    Use with `-a` option to perform all possible types of scan.

- [__Steganography Online__](https://stylesuxx.github.io/steganography/): Straightforward simple encode and decode tool.

- [__StegOnline__](https://georgeom.net/StegOnline/upload): Useful website with multiple tools, including viewing color planes, bit planes, and LSB plane. Web version of `stegsolve`. Contains a checklist for solving steganography challenges, along with example writeups.

- [__Aperi'Solve__](https://www.aperisolve.com/): Multi-tool online that performs scan using multiple tools.

    >[!WARNING]
    > Online tools might not work for large image files and PNG files.

- [`stegsolve`](https://github.com/Giotino/stegsolve): Modified version of the original `stegsolve`. Java offline tool. Can browse color and bit planes, alpha plane, etc.

- [`stepic`](https://pypi.org/project/stepic/): Python's library for steganography. Some images might need `stepic` specifically to work. Example:

    ```python
    from PIL import Image
    import stepic
    img = Image.open('file.png')
    print(stepic.decode(img))
    ```

>[!NOTE]
> Some tools might only work for JPEG or PNG and not the other format. See the documentation of each tool for more.

## 4. PNG-specific tools

Tools for checking PNG file specifically:

- `pngcheck`: Check for corruption in PNG images.

    Can use `pngcheck -vtp7f filename.png` to view more information.

- [`png-unhide`](https://github.com/ryanking13/png-unhide): Check and fix inconsistency of metadata and actual image, for example when the image is bigger than what the metadata (`IHDR` section of the PNG file) says. A copy of the script is included on [this page](/forensics/png-unhide.html).

    >[!TIP]
    > Use this tool when you see "Too much data" errors when trying to convert the PNG file to JPG file or when trying to read the file using OpenCV (Python).

- It might also be useful to try converting the image to JPEG using ImageMagick.

<!-- ## JPEG-specific tools

Tools for  -->

## 5. Data hidden in RGBA values

Data can be hidden in RGBA values of an image. Use the StegOnline tool or a Python script (Jupyter notebook recommended) to view pixel values data.

## 6. Audio tools

Tools for audio files:

- __Sonic Visualizer__: View wave, spectrogram, etc. of audio files. To see spectrogram, go to View &rarr; Add panes &rarr; Spectrogram (menu names might be different).

## 7. More advanced steganography

See [StegOnline's checklist](https://georgeom.net/StegOnline/checklist) (specifically sections 10 and 11) for advanced techniques.