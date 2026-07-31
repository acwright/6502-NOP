6502-NOP
========

This is a simple ROM for the [A.C. Wright 6502](https://github.com/acwright/6502-ACE) family of computer systems, filled with NOPs (`$EA`) so that it does nothing (NOP = No Operation).

It is a hardware bring-up aid: with this ROM fitted the CPU free-runs through the whole address space, so the address lines, decode logic and bus can be probed without any firmware behaviour in the way.

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

## Related

- [6502-ACE](https://github.com/acwright/6502-ACE) — the hardware, and the index of the whole family
- [6502-BIOS](https://github.com/acwright/6502-BIOS) — the real firmware to fit once the board checks out
- [6502-WOZMON](https://github.com/acwright/6502-WOZMON) — a minimal but usable ROM, the next step up from this one

## License

MIT License — see [LICENSE](LICENSE).
