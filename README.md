# Pre-defined C/C++ compiler macros

Lists of pre-defined macros for various compilers.

You should probably check the [Pre-defined C/C++ Compiler Macros
wiki](https://sourceforge.net/p/predef/wiki/Home/) on SourceForge
first. It's probably more useful for now; it has lots more compilers,
and a more friendly presentation. This repo, OTOH, has more complete
information (all of the pre-defined macros instead of just a select
few).

If you have access to compilers not listed, a PR would be appreciated!

## Generating the files

* GCC:
  * C: `gcc -dM -E -o "${OUTFILE}" empty.c`
  * C++: `g++ -dM -E -o "${OUTFILE}" empty.cpp`
* clang:
  * C: `clang -dM -E -o "${OUTFILE}" empty.c`
  * C++: `clang++ -dM -E -o "${OUTFILE}" empty.cpp`
* Intel C/C++ Compiler:
  * C: `icc -dM -E -o "${OUTFILE}" empty.c`
  * C++: `icpc -dM -E -o "${OUTFILE}" empty.cpp`
* Oracle Developer Studio:
  * C: `suncc -xdumpmacros=%all -E empty.c 2>&1 | grep -oP '#define .+' > "${OUTFILE}"`
  * C++: `sunCC -xdumpmacros=%all -E empty.cpp 2>&1 | grep -oP '#define .+' > "${OUTFILE}"`
* PGI C/C++ Compiler:
  * C: `pgcc -dM -E /dev/null > "${OUTFILE}"`
  * C++: `pgc++ -dM -E /dev/null > "${OUTFILE}"`
* TI C/C++ Compiler:
  * C: `cl6x --preproc_macros empty."$MODE" --output_file="$OUTFILE"`
  * C++: `cl6x --preproc_macros empty."$MODE" --output_file="$OUTFILE"`
* Emscripten:
  * C: `emcc -dM -E -o "${OUTFILE}" empty.c`
  * C++: `em++ -dM -E -o "${OUTFILE}" empty.cpp`
