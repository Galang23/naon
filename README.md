# naon 🌴

**naon** (Sundanese for "what") is a prank version of the Unix `file` utility that outputs file type descriptions in Sundanese language.

Perfect for when someone mistypes `nano` as `naon`! 😄

## Demo

```bash
$ naon /bin/ls /etc/passwd /tmp
/bin/ls:     program ELF 64-bit LSB pie, bisa dijalankeun
/etc/passwd: téks ASCII, naon atuh ieu téh?
/tmp:        ieu téh polder, lain file atuh!
```

vs original `file`:

```bash
$ file /bin/ls /etc/passwd /tmp
/bin/ls:     ELF 64-bit LSB pie executable, x86-64...
/etc/passwd: ASCII text
/tmp:        sticky, directory
```

## Translation Examples

| File Type | Original | Sundanese |
|-----------|----------|-----------|
| Text file | ASCII text | téks ASCII, naon atuh ieu téh? |
| Binary | ELF 64-bit executable | program ELF 64-bit, bisa dijalankeun |
| Directory | directory | ieu téh polder, lain file atuh! |
| PNG | PNG image data | gambar PNG, sae pisan euy! |
| Archive | gzip compressed data | data dikompres ku gzip, rame euy! |
| Library | shared object | pustaka nu dibagikeun |
| Unknown | *any type* | *type*, naon ieu téh? |

## Installation

### From Source

```bash
git clone https://github.com/galang23/naon.git
cd naon
./configure --prefix=/opt/naon --program-transform-name='s/file/naon/'
make -j$(nproc)
sudo make install
```

### Optional: Add to PATH

```bash
echo 'export PATH="/opt/naon/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Now whenever someone types `naon` instead of `nano`, surprise! 🎉

## Uninstall

```bash
sudo rm -rf /opt/naon
# Remove the PATH line from ~/.bashrc
```

## How It Works

Modified `file_getbuffer()` in `src/funcs.c` to transform English output to Sundanese. Only ~80 lines added, detection logic unchanged.

## Dependencies

- gcc, autoconf, automake, libtool
- zlib, libbz2, liblzma, libzstd (optional)

## License

BSD-style (same as original file utility)

---

*"naon" = "what" in Sundanese. "Naon ieu téh?" = "What is this?"*

---

## Original file(1) Documentation

This is Release 5.x of Ian Darwin's (copyright but distributable)
file(1) command, an implementation of the Unix File(1) command.
It knows the 'magic number' of several thousands of file types.

- Home page: https://www.darwinsys.com/file/
- Public repo: https://github.com/file/file
- Download link: <ftp://ftp.astron.com/pub/file/>

### Source Files

* `src/file.c` - the main program
* `src/funcs.c` - utility functions (contains naon translation)
* `src/magic.c` - the libmagic api
* `src/softmagic.c` - magic file based tests
* `src/ascmagic.c` - ASCII detection tests
* `magic/` - directory of magic file pieces

See the original file README for complete documentation.
