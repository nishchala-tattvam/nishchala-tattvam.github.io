# GoogleTest
## Hello world

```cpp linenums="1"
#include <gtest/gtest.h>

int Factorial(int n);

// Tests factorial of 0.
TEST(FactorialTest, HandlesZeroInput) {
  EXPECT_EQ(Factorial(0), 1);
}

// Tests factorial of positive numbers.
TEST(FactorialTest, HandlesPositiveInput) {
  EXPECT_EQ(Factorial(1), 1);
  EXPECT_EQ(Factorial(2), 2);
  EXPECT_EQ(Factorial(3), 6);
  EXPECT_EQ(Factorial(8), 40320);
}
```

## Simple test macro

```cpp linenums="1"
TEST(TestSuiteName, TestName) {
  ... statements ...
}
```

## Fixtures
### Initiation

```cpp linenums="1"
class TestFixtureName : public testing::Test {
 protected:
  TestFixtureName() {
        ... some common logic ...
  }

... shared data members ...
};
```

### Fixture macros

```cpp linenums="1"
TEST_F(TestFixtureName, TestName) {
  ... statements ...
}
```

## Assertions

```cpp linenums="1"
EXPECT_EQ(val1, val2)
EXPECT_THROW(statement, exception_type)
```

## References

- [GoogleTest documentations]
- [GoogleTest source code]

  [GoogleTest documentations]: https://google.github.io/googletest/
  [GoogleTest source code]: https://github.com/google/googletest

