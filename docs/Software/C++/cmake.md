# cmake

## Installation
=== "Ubuntu"
    First, set up [cmake APT repository] from kitware.

      [cmake APT repository]: https://apt.kitware.com/

    Then, 
    
    ```console
    $ sudo apt-get install cmake
    ```

## Common operations

### Generate a build system in a dir called build

```console
$ cmake -B build
```

### Build the project

```console
$ cmake --build build
```

### Run the executable

```console 
$ ./build/hello
```

## Common CMLs
### Building an executable

```cmake linenums="1" 
add_executable(MyProgram)

target_sources(MyProgram
  PRIVATE
    main.ccc
)
```

### Building a library

```cmake linenums="1"
add_library(MyLibrary)

target_sources(MyLibrary
  PRIVATE
    library_implementation.cc

  PUBLIC
    FILE_SET HEADERS
    BASE_DIRS
      include
    FILES
      include/library_header.h
)
```

??? info "BASE_DIRS"
    `BASE_DIRS` tells the compiler where to look for header files.
    Consider the following project structure,

    ```text
    .
    ├── CMakeLists.txt
    ├── include
    │   └── mylibrary
    |       └── hello.h
    └── src
        └── hello.cc
    ```

    === "Without specifying `BASE_DIRS`"

        ```cpp linenums="1" title="hello.cc"
        #include "mylibrary/include/hello.h"
        ```

    === "With `BASE_DIRS`"

        ```cpp linenums="1" title="hello.cc"
        #include "mylibrary/hello.h"  // This is the more common approach.
        ```

    The purpose of `BASE_DIRS` is **not** a shorthand/prefix for filepaths in `FILES`.
    We still need to specify the full path relative to the CML in the arguments of `FILES`.



### Linking together libraries and executables

```cmake linenums="1" 
target_link_libraries(MyProgram
        MyLibrary
)
```

### Including CML in subdirectories

Consider the following folder structure

```text
.
├── CMakeLists.txt
└── tests
    ├── CMakeLists.txt
    └── hello_test.cc
```

We may include `tests/CMakeLists.txt` in the root CML by adding

```cmake linenums="1"
add_subdirectory(tests)
```

??? info "Relative paths in subdirectory CML"
    The filepath in the subdirectory CML is relative to the subdirectory CML not the root CML.
    In our example,

    ```cmake linenums="1" title="tests/CMakeLists.txt"
    add_executable(
          hello_test
          hello_test.cc
    )
    ```

    is the correct reference to `hello_test.cc`
  
### Using external libraries
#### Load the `FetchContent` module

```cmake linenums="1"
include(FetchContent)
```

#### Adding a git repository

```cmake linenums="2"
FetchContent_Declare(
    tomlplusplus
    GIT_REPOSITORY https://github.com/marzer/tomlplusplus.git
    GIT_TAG v3.4.0
)
```
<!-- FetchContent_MakeAvailable(tomlplusplus) -->

#### Adding a zip file via URL

```cmake linenums="7"
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
```

#### Make external library available to project

```cmake linenums="11"
FetchContent_MakeAvailable(tomlplusplus googletest)
```

## References

- [Tutorial]

  [Tutorial]: https://cmake.org/cmake/help/latest/guide/tutorial/index.html