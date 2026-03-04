6502-NOP
========

This is a simple ROM for the [A.C. Wright 6502 project](https://github.com/acwright/6502) filled with NOPs (`$EA`) that does nothing (NOP = No Operation).

## Prerequisites

### Install cc65 Toolchain

The cc65 toolchain provides the assembler and linker needed to build 6502 assembly code.

macOS (using Homebrew):
```bash
brew install cc65
```

Linux (Debian/Ubuntu):
```bash
sudo apt-get install cc65
```

Other platforms: See [cc65 documentation](https://cc65.github.io/)

### Optional: Install minipro (for EEPROM burning)

Only required if you plan to program an AT28C256 EEPROM chip:
```bash
brew install minipro
```

## Building

Build the ROM image:
```bash
make
```

This generates:
- `NOP.bin` - 32KB ROM image ($8000-$FFFF) filled with NOP instructions ($EA)
- `NOP.lst` - Assembly listing file for debugging

## Verification

View the generated binary as hex dump:
```bash
make view
```

You should see a file filled with `ea` bytes (the NOP opcode).

## Programming EEPROM

To burn the ROM to an AT28C256 EEPROM chip using a TL866 programmer:
```bash
make eeprom
```

**Note:** This requires a TL866 (or compatible) programmer and the minipro software.

## Cleaning Build Artifacts

Remove generated files:
```bash
make clean
```
