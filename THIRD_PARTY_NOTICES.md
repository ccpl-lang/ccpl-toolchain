# Third party notices

This repository redistributes the following third party software.

## TinyCC

* Version: 0.9.27, Windows x64 build
* Homepage: <https://bellard.org/tcc/>
* License: GNU Lesser General Public License, version 2.1
* License text: `third_party/tcc/COPYING.LESSER`
* Files: everything under `tcc/`, including `tcc.exe`,
  `i386-win32-tcc.exe`, `libtcc.dll`, `libtcc/`, `include/`, and `lib/`

TinyCC is distributed here unmodified, only as the backend that `coolc.exe`
runs to turn generated C into native programs.

TinyCC is free software. You can redistribute it and modify it under the terms
of the GNU Lesser General Public License as published by the Free Software
Foundation, either version 2.1 of the License or any later version. TinyCC is
distributed in the hope that it will be useful, but without any warranty,
including the implied warranty of merchantability or fitness for a particular
purpose. See the GNU Lesser General Public License for more details.

The source archive for the bundled TinyCC release is available from
<https://bellard.org/tcc/>.

Because TinyCC is a separate program invoked as an external tool by `coolc.exe`,
its LGPL licensing does not affect the license of the CCPL compiler. The
compiler and runtime are licensed under the GNU GPL v3. See `LICENSE`.

## CCPL compiler and runtime

* License: GNU General Public License, version 3
* License text: `LICENSE`
* Files: `coolc.exe`, `clm.exe`, `runtime.h`, `coolc.bat`, `clm.bat`,
  `hello.ccpl`

Copyright (C) 2026 The CCPL Authors.