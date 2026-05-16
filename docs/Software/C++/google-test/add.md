# Adding `googletest` to your project
## Via Bazel
## Via CMake
### Fetch `googletest`

```cmake linenums="1"
include(FetchContent)
FetchContent_Declare(
        googletest
        GIT_REPOSITORY https://github.com/google/googletest.git
        GIT_TAG v1.17.0
)
FetchContent_MakeAvailable(googletest)
```

### Enable testing

```cmake linenums="8"
enable_testing()

add_executable(
        hello_test
        hello_test.cc
)
target_link_libraries(
        hello_test
        GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)
```