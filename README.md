# ccpl toolchain

**Ready to run CCPL for Windows.** This bundle contains the compiler, the
package manager, the runtime, and TinyCC in one folder. Unzip it, write a
`.ccpl` file, and get a native program.

Version 0.4.0.

## What is in the bundle

```text
ccpl-toolchain/
  coolc.exe              the CCPL compiler
  clm.exe                the package manager
  coolc.bat              convenience launcher for coolc
  clm.bat                convenience launcher for clm
  runtime.h              runtime injected into compiled programs
  hello.ccpl             a small example
  tcc/                   TinyCC, including headers and libraries
  third_party/tcc/       third party license notices
  THIRD_PARTY_NOTICES.md
  LICENSE                GNU GPL v3
```

## Contents

* [What is in the bundle](#what-is-in-the-bundle)
* [Requirements](#requirements)
* [Usage](#usage)
* [Command line](#command-line)
* [Package manager](#package-manager)
* [Example](#example)
* [Foreign functions](#foreign-functions)
* [What is CCPL](#what-is-ccpl)
* [Updating this bundle](#updating-this-bundle)
* [License](#license)

## Requirements

* Windows 10 or newer, on x64.
* Nothing else. TinyCC is bundled.
* Python and a C++ compiler are optional, and only needed for the Python and
  C++ foreign function features.

## Usage

```bat
coolc.bat hello.ccpl --run
```

Or call the compiler directly:

```bat
coolc.exe hello.ccpl -o hello.exe --fast
```

`coolc.exe` finds `runtime.h` and `tcc\tcc.exe` relative to itself, so the whole
folder can be moved anywhere or added to `PATH`.

## Command line

```text
coolc <source.ccpl> [-o out.exe] [--run] [--fast] [--show-c]
```

* `-o, --output <file>` sets the output program path.
* `--run` runs the program after a successful build.
* `--fast` compiles the generated C with `-O2 -s`.
* `--show-c` prints the generated C and exits.
* `--version, -v` prints the compiler version.
* `-h, --help` prints usage.

## Package manager

`clm` installs libraries for `get`:

```bat
clm.bat search math
clm.bat install <name>
clm.bat list
clm.bat remove <name>
```

Packages go to `packages\` next to the compiler. The registry can be changed
with the `CLM_REGISTRY` environment variable.

## Example

```ccpl
say("hello, world")

var name = "CCPL"
var year = 2026
say("welcome to", name, "in", year)
```

```text
> coolc.bat hello.ccpl --run
hello, world
welcome to    CCPL    in    2026
```

## Foreign functions

This bundle supports C, C++, and Python calls:

```ccpl
extern "c" func strlen(s: cstr): u64 from "msvcrt.dll"
say(strlen("hello"))
```

See the main repository documentation at
<https://github.com/ccpl-lang/ccpl/blob/main/docs/ffi.md>.

## What is CCPL

CCPL is a small, Lua flavored language with optional native C types that
compiles to a native program through TinyCC.

* Compiler and language implementation:
  <https://github.com/ccpl-lang/ccpl>
* VS Code syntax extension: <https://github.com/ccpl-lang/vscode-ccpl>

## Updating this bundle

This repository mirrors build outputs of the compiler. To refresh it:

1. Build the compiler and `clm` with `build.bat` in the compiler repository.
2. Copy `coolc.exe`, `clm.exe`, and `runtime.h` here.
3. Keep `runtime.h` byte for byte identical to `src\runtime.h` in the compiler
   repository.
4. Run `coolc.bat hello.ccpl --run` as a smoke test.

The CI workflow checks that the bundled programs run and that `runtime.h`
matches the compiler source on the main branch.

## License

The CCPL compiler and runtime are licensed under the GNU General Public License,
version 3. See `LICENSE`.

This bundle also distributes TinyCC, which is licensed under the GNU Lesser
General Public License, version 2.1. Its license is preserved at
`third_party/tcc/COPYING.LESSER`, and details are in `THIRD_PARTY_NOTICES.md`.
TinyCC is distributed unmodified. The source archive for the bundled TinyCC
release is available from <https://bellard.org/tcc/>.