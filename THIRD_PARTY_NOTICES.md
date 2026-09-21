# Third-party notices

This repository redistributes the following third-party software.

## TinyCC (TCC)

- **Version:** 0.9.27 (Windows build)
- **Homepage:** <https://bellard.org/tcc/>
- **License:** GNU Lesser General Public License, version 2.1
- **License text:** [`third_party/tcc/COPYING.LESSER`](third_party/tcc/COPYING.LESSER)
- **Files:** everything under [`tcc/`](tcc/) — including `tcc.exe`,
  `i386-win32-tcc.exe`, `libtcc.dll`, `libtcc/`, `include/` and `lib/`.

TinyCC is distributed here **unmodified**, solely as the backend used by `coolc.exe`
to turn generated C into native executables.

TinyCC is free software; you can redistribute it and/or modify it under the terms of
the GNU Lesser General Public License as published by the Free Software Foundation,
either version 2.1 of the License, or (at your option) any later version. TinyCC is
distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without
even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU Lesser General Public License for more details.

Because TinyCC is a separate program invoked as an external tool by `coolc.exe`, its
LGPL licensing does not affect the license of the CCPL compiler itself. The compiler
and runtime are licensed under the GNU GPL v3; see [`LICENSE`](LICENSE).

## CCPL compiler and runtime

- **License:** GNU General Public License, version 3
- **License text:** [`LICENSE`](LICENSE)
- **Files:** `coolc.exe`, `runtime.h`, `coolc.bat`, `hello.ccpl`

Copyright (C) 2026 The CCPL Authors.
