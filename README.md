# ccpl-toolchain

**Ready-to-run CCPL toolchain for Windows** â€” the compiler, its runtime and
[TinyCC](https://bellard.org/tcc/) in one folder. Unzip, write a `.ccpl` file, get a
native `.exe`.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.3.0-informational.svg)](https://github.com/ccpl-lang/ccpl/releases)
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6.svg)](#requirements)
[![Bundles TinyCC](https://img.shields.io/badge/bundles-TinyCC-lightgrey.svg)](THIRD_PARTY_NOTICES.md)

## Contents

```
ccpl-toolchain/
â”œâ”€â”€ coolc.exe              # the CCPL compiler
â”œâ”€â”€ coolc.bat              # convenience launcher
â”œâ”€â”€ runtime.h              # runtime injected into compiled programs
â”œâ”€â”€ hello.ccpl             # a small example
â”œâ”€â”€ tcc/                   # TinyCC (compiler, headers, libs)
â”œâ”€â”€ third_party/tcc/       # third-party license notices
â”œâ”€â”€ THIRD_PARTY_NOTICES.md
â””â”€â”€ LICENSE                # GNU GPL v3
```

## Requirements

- Windows (32- or 64-bit).
- Nothing else â€” TinyCC is bundled.

## Usage

```bat
coolc.bat hello.ccpl --run
```

or call the compiler directly:

```bat
coolc.exe hello.ccpl -o hello.exe --fast
```

| Flag | Meaning |
| --- | --- |
| `-o, --output <file>` | Output executable path. |
| `--run` | Run the executable after a successful build. |
| `--fast` | Compile the generated C with `-O2 -s`. |
| `--show-c` | Print the generated C and exit. |
| `--version, -v` | Print the compiler version. |
| `-h, --help` | Show usage. |

`coolc.exe` locates `runtime.h` and `tcc\tcc.exe` relative to itself, so you can move
the whole folder anywhere (or add it to `PATH`) and it keeps working.

## Example

`hello.ccpl`:

```ccpl
-- hello world in CCPL
say("hello, world")

variable lang = "CCPL"
var year = 2026
say("welcome to", lang, "- compiled straight to a native .exe")
say("the time is year", year)
```

```bat
> coolc.bat hello.ccpl --run
hello, world
welcome to      CCPL    - compiled straight to a native .exe
the time is year        2026
```

## What is CCPL?

CCPL is a small, Lua-flavored language with optional native C types that compiles to
a native executable through TinyCC. See the main compiler repository for the language
reference and source:

- **ccpl** â€” compiler and language implementation: <https://github.com/ccpl-lang/ccpl>
- **vscode-ccpl** â€” VS Code syntax highlighting: <https://github.com/ccpl-lang/vscode-ccpl>

## Updating the toolchain

This repository mirrors build outputs of the compiler. To refresh it:

1. Build the compiler (`build.bat` in the `ccpl` repo).
2. Copy the new `coolc.exe` and `runtime.h` here.
3. Keep `runtime.h` byte-for-byte identical to the compiler's copy.

## License

The CCPL compiler and runtime are licensed under the **GNU GPL v3** (see [LICENSE](LICENSE)).

This bundle also distributes **TinyCC**, which is licensed under the **GNU LGPL v2.1**.
Its license is preserved at [`third_party/tcc/COPYING.LESSER`](third_party/tcc/COPYING.LESSER);
see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for details. TinyCC is distributed
unmodified.
