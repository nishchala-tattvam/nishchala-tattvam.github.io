# C++ language features

## Basic types

### Introduction
Fundamental variable types in C++ are:

- `int`
- `float`
- `double`
- `char`
- `bool`

```c++ title="Initialising variables with default values" linenums="1"
int a{};    // a = 0
float b{}; // b = 0
double c{};    // c = 0
char d{};  // d = '\0'
bool e{};  // e = 0
```

```c++ title="Initialising variables with custom values" linenums="1"
int a = 9;    
float b = 123.4; 
double c = 123.4;    
char d = "H";  
bool e = true;  
```

??? failure "Declare variables without an initial value"
    In C++, you can declare variables without an initial value. 

    ```c++ linenums="1"
    int x;
    ```
    However, this is discouraged as it leads to undefined behaviour.

    ```c++ linenums="2"
    std::cout << x << std::endl;
    ```

    !!! info "Output"
        === "Ubuntu"
            ```text
            32767
            ```
        
        === "macOS"
            ```text
            1
            ```

We may check the size of variables with `sizeof`. It prints out the size of the
variable in bytes.

```c++ title="Checking variable size" linenums="1"
int a{};
std::cout << sizeof(a) << std::endl;
```

!!! info "Output"

    ```text
    4
    ```

The size of fundamental types is implementation defined, but common values are

| Type        | Size    |
|-------------|---------|
| `int`       | 4 bytes |
| `float`     | 4 bytes |
| `double`    | 8 bytes |
| `char`      | 1 byte  |
| `bool`      | 1 byte  |

### `int`
We have seen the most basic int literal

```c++ linenums="1"
int a = 42;
```
Additionally, we may use `'` to separate digits for readability.

```c++ linenums="1"
int a = 36'000'000;
```
Moreover, we may pass in digits as binary or hexadecimal.

```c++ linenums="1"
int a = 0x3fff; // 16383 in decimal
int b = 0b0011111111111111; // Also 16383 in decimal
```

By default, `int` is signed 32-bits in C++. To signal the integer is unsigned, we
may use `unsigned` (also 32-bits). In this case, we shall add suffix `u`.

```c++ linenums="1"
unsigned a = 42u;
```

To represent integers beyond 2 bn, (maximum of `int`), we may use the 64-bit signed
integer, `long`. It can represent numbers up to 9 quintillion (18 zeros).
In this case, we shall add suffix `l`.

```c++ linenums="1"
long a = 42l;
```

We can also use `unsigned long` etc., and add the corresponding suffix.
```c++ linenums="1"
unsigned long val_3 = 0776745ul;
```

Although we are almost guaranteed to find `int` to be 32-bit, `long` to be 64-bit in
most modern systems, it is not guaranteed. To ensure a number to be of certain bits,
we need to use **Fixed width integer types**.

- `int64_t`
- `uint32_t`
- ...


??? info "Equivalent types"

    - `int`: `signed`
    - `unsigned int`: `unsigned`

## Advanced types
### Enumerators

```cpp linenums="1" title="Example"
enum priority = {LOW, NORMAL, HIGH}

int main() {
  enum Level a = NORMAL;
  std::cout << a << std::endl;
}
```

```text title="Output"
1
```

## Control flows 
### `if-else`

```c++ linenums="1" title="if-else statement"
int a;
std::cout << "Enter a number: ";
std::cin >> a;

if (constexpr int b = 0; a == 99) {
    std::cout << "Congrats you hit the jackpot!" << std::endl;
} else if (a > b) {
    std::cout << a << " is greater than " << b << std::endl;
} else if (a < b) {
    std::cout << a << " is less than " << b << std::endl;
} else {
    std::cout << a << " is equal to " << b << std::endl;
}
```

### `for`

```c++ linenums="1" title="Postfix for loop"
for (int i = 0; i < 5; i++) {
    std::cout << i << std::endl;
}
```

```c++ linenums="1" title="Prefix for loop"
for (int i = 0; i < 5; ++i) {
    std::cout << i << std::endl;
}
```

!!! note "Prefix vs Postfix"
    `a++` is known as postfix: add `1` to `a`, returns the *old* value. `++a` is 
    known as prefix: add `1` to `a`, returns the *new* value. 

```c++ linenums="1" title="Range-based for loop"
for (const int i: {1, 2, 3, 4, 5}) {
    std::cout << i << std::endl;
}
```

### `while`

```c++ linenums="1" title="while loop"
int i = 0;
while (i < 10) {
    std::cout << i++ << std::endl;
}
```

```c++ linenums="1" title="do-while loop"
int j = 0;
do {
    std::cout << j++ << std::endl;
} while (j < 5);
```

!!! note "`while` vs `do-while`"
    `while` loop is entry controlled: the content of the loop will be executed
    only if the condition(s) is(are) met. `do-while` loops are exit controlled.
    The content is garanteed to be executed at least once.

### Logical and comparison expressions

```text linenums=1 title="Logical expressions"
- a && b
- a || b
- !a
```

```text linenums=1 title="Comparison expressions"
- a == b, a != b
- a > b, a < b
- a >= b, a <= b
```

## Functions
### Passing by references

The following code results in error: ambiguous function call.

```cpp linenums=1
int compute(int &a) {
    return a + 10;
}

int compute(int a) {
    return a + 10;
}

int main() {
    int b{99};
    std::cout << compute(b) << std::endl;
}
```

## Classes
### Member Initializer List

```cpp linenums=1
struct S
{
    S(): m{42} {}
    S(int a): m{a} {}
    int m;
};
```

### The rule of three/five/zero

```cpp linenums="1" title="A rule of five example"
class Person {
private:
    char* name_;

public:
    Person(const char* n) {
        name_ = new char[strlen(n) + 1];
        strcpy(name_, n);
    }

    // Copy constructor
    Person(const Person& p) {
        name = new char[strlen(p.name_) + 1];
        strcpy(name_, p.name_);
    }

    // Copy assignment operator
    Person& operator=(const Person& p){
        delete[] name_;          
        name_ = new char[strlen(p.name_) + 1];  
        strcpy(name_, p.name_);   

        return *this;
    }

    // Move constructor
    Person(const Person&& p) noexcept {
        name_ = new char[strlen(p.name_) + 1];
        name_ = std::move(name_);
    }

    // Move assignment operator
    Person& operator=(const Person &&p) noexcept{
        delete[] name_;          
        name_ = new char[strlen(p.name_) + 1];  
        name_ = std::move(name_);
        
        return *this
    }


    ~Person() {
        delete[] name_;
    }
};

int main() {
    Person p1("Alice");
    Person p2 = p1;   // deep copy

    p1.display();
    p2.display();
}
```

#### References

- [Homepage]

  [Homepage]: https://en.cppreference.com/cpp/language/rule_of_three

### `const` member functions
`const` member functions are functions which do not modify the object.
For example, consider a class describing a radioactive source.

```c++
class Source {
private:
  std::string name_{}; // Source name. e.g. Na-22, Cs-136, Co-92
public:
  Source(std::string name){
      name_ = name;
  }
  [[nodiscard]] std::string name() const;
```

In this setup, we have a getter that does not modify the object so it makes sense to mark it as `const`.
`[[nodiscard]]` tells the compiler to issue a warning if the function is called 
but the return value is not used.
For example,

```c++
Source source("Na-22");

std::string name = source.name();   // This is ok.
source.name();  // Compiler will issue a warning.
```

### References

- [GeekforGeeks article]
- [StackOverflow post]

  [GeekforGeeks article]: https://www.geeksforgeeks.org/cpp/const-member-functions-c/
  [StackOverflow post]: https://stackoverflow.com/questions/3141087/what-is-meant-with-const-at-end-of-function-declaration

## Templates 

```c++ title="function templates"  linenums="1"
template <typename T>
T Add(T a, T b) {
  return a + b;
}

int main() {
  std::cout << Add<int>(5, 3) << "\n";
  std::cout << Add<double>(2.5, 1.5) << "\n";
  return 0;
}
```

```c++ title="function templates"  linenums="1"
template <typename To, typename From>
To Add(From a, From b) {
  return a + b;
}

int main() {
  std::cout << Add<int>(5, 3) << "\n";
  std::cout << Add<double>(2.5, 1.5) << "\n";
  return 0;
}
```

```c++ title="class templates" linenums="1"
template <typename T>
class Box {
  public:
    T value;
    Box(T v) {
      value = v;
    }
    void show() {
      std::cout << "Value: " << value << "\n";
    }
};

int main() {
  Box<int> int_box(50);
  Box<std::string> str_box("Hello");

  int_box.show();
  str_box.show();
  return 0;
}
```

## Memory management
Pointers are the memory address of an object.

```c++ linenums="1"
int num = 4;

int* ptr = &num; // ptr is a pointer
std::cout << ptr << std::endl;  // Output: 0x16d06ee3c
```

We may access the value stored in `ptr` by _pointer 
dereferencing_,`*ptr`. `*ptr` returns the value stored in the pointer.

```cpp linenums="5"
std::cout << *ptr << std::endl;  // Output: 4
```

By declaring a raw pointer, we manually allocate memory in our program.

```c++ linenums="1"
int* ptr = new int;
```

This first `int` signals `ptr` points to an integer, while the second `int`
tells to compiler to allocate memory space for an integer to `ptr`. Memory
allocated via the `new` keyword must be manually freed with `delete`.

```c++ linenums="2"
delete ptr;
```

In modern c++, raw pointers are rarely used. Instead, smart pointers are preferred as they handle memory deallocation for us.

```cpp linenums="1"
std::unique_ptr<LargeObject> pLarge(new LargeObject());
```

### References

- [Microsoft lean's article about smart pointers]

  [Microsoft lean's article about smart pointers]: https://learn.microsoft.com/en-us/cpp/cpp/smart-pointers-modern-cpp?view=msvc-170

### Move semantics
A special function `std::move()` takes in a `rvalue` as an argument and turns it into a `xvalue`.

## RegEx
Regex is provided by `<regex>` in the standard library.

```cpp linenums="1"
#include <regex>
```

## References
- [An excellent post] that answers some of the common questions about C++.
- [Const correctness from ISOC++] 

  [Const correctness from ISOC++]: https://isocpp.org/wiki/faq/const-correctness
  [An excellent post]: https://news.ycombinator.com/item?id=16197127