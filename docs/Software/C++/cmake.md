# cmake
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

```text linenums="1" 
add_executable(MyProgram)

target_sources(MyProgram
  PRIVATE
    main.ccc
)
```

### Building a library

```text linenums="1"
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

### Linking together libraries and executables

```text linenums="1" 
target_link_libraries(MyProgram
        MyLibrary
)
```

## References

- [Tutorial]

  [Tutorial]: https://cmake.org/cmake/help/latest/guide/tutorial/index.html