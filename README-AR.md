# libmagic for Windows 64 bit
*A. Reeves, 15 Aug 2019*

Binaries (dlls) were obtained from <https://github.com/pidydx/libmagicwin64>.  Unfortunately, this repository contains no source code.

Source code is available in these two repositories:
  - <https://github.com/nscaife/file-windows>
  - <https://github.com/file/file>

The repository from pidydx did not include a header or a lib file.

For the header file, I used magic.h.in from <https://github.com/file/file>, which seems to work.

I generated the lib file using dumpbin.exe from Visual Studio and MinGW's dlltool.exe:

```
dumpbin.exe /exports magic1.dll
dlltool.exe -d magic1.def -l magic1.lib -D magic1.dll
```

There are open-source alternatives to dumpbin.exe, the name of which currently escapes me...

lib.exe (from Visual Studio) could be used instead of dlltool, but my version of Visual Studio is 32-bit only.  dlltool allows users to specify the machine type, with a default of i386:x86-64.