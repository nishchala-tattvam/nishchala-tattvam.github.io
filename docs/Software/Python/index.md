# Python language features

## Variables 
Fundamental types in Python are

- `int`
- `float`
- `complex`
- `str`
- `list`
- `dict`

However, Python is an interpreted language, so all variables are dynamically typed.
```python title="Initialisation variables in Python" linenums="1"
a = 99
b = 1 + 2j
c = "Hello"
d = True
```
Optionally, we can add type hint to the variable.
```python title="Type hinting in Python" linenums="1"
a: int = 123
```
??? failure "Bad declaration"
    Sometimes, we will see code like
    ```python linenums="1"
    a = int
    ```
    In this case, we just assign `a` the class `int`. We can even type hint with `a`.
    ```python linenums="2"
    b: a = 99
    ```
We may use `type` to check the type of variables.
```python title="Check the type of variables" linenums="1"
a = 99
type(a)
```
!!! info "Output"
    ```text
    int
    ```

```python title="Digit seperators" linenums="1"
a = 1_000_000
```