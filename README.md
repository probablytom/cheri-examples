# cheri-examples
cheri-riscv sample c programs

------
## Build instructions with CMake
Build all the example code with CMake using default settings :
1. Create a separate build directory (\<build-dir\>) outside the source directory (\<source-dir\>).
2. Generate the build files using either **Unix Makefiles** (*default*) or **Ninja** (specfied
   with **-G**). Currently only the *RISC-V* cheri-purecap toolchain file has been created.
   1. If executing from inside the build directory :

   `cmake -DCMAKE_TOOLCHAIN_FILE=riscv64-purecap.cmake <relative-path-to-source-dir>`

   2. If executing from outside the build directory :

   `cmake -B <build-dir> -S <source-dir> -DCMAKE_TOOLCHAIN_FILE=riscv64-purecap.cmake`

3. Build all the examples
   1. If executing from inside the build directory,  `make all` *OR* `ninja all`
   2. If executing from outside the build directory, `cmake --build <build-dir>`

#### CMake options:
* **-DCMAKE_TOOLCHAIN_FILE**: Use `-DCMAKE_TOOLCHAIN_FILE=<toolchain-file>` to select
  architecture to compile binary for. Only *riscv64-purecap.cmake* is currently supported.
* **-DSDK**: Use `-DSDK=<source-to-sdk>` to point to the *CHERI* SDK directory.
  (Default path: ${HOME}/cheri/output/sdk)
* **-G**: Choose preferred build system
  - Use `-G "Unix Makefiles"` to build using *makefiles* (*default*).
  - Use `-G Ninja` to build using *ninja*.
