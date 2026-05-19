# `gcc` and `make`
C++ is a compiled language.
The GNU Compiler Collection (GCC) is a set of compilers for programming languages,
including C, C++, Assembly, and many more. It is the de facto standard in Linux
environments and is used to compile both the GNU toolchain and the Linux kernel.

## Installation
=== "Ubuntu"
    We install build tools via `apt`. To install GCC.

    ```console
    $ sudo apt install gcc g++
    ```
    
    We may specify to install specific versions of GCC.
    For example,

    ```console
    $ sudo apt install g++-13
    ```

    To install `make`,

    ```console
    $ sudo apt install make
    ```

    An alternative, but common approach is to install the `build-essential` 
    package, which is a collection of common tools including `gcc`, `g++`, and `make`.

=== "macOS"
    On macOS, 

    ```console
    $ xcode-select --install
    ```

    would install both GCC and make.

    If you want a specific version of `g++`, you may install it via Homebrew.
    For example,

    ```console
    $ brew install gcc@13
    ```
    
## References

- [The ubuntu guide]

  [The ubuntu guide]: https://documentation.ubuntu.com/ubuntu-for-developers/howto/gcc-setup/#install-gcc