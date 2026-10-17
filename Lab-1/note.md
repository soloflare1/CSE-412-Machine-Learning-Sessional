# Topic: `print()`, `sep`, `end`, `input()`, `int()`, `if-else`, and `for` loops

# 1. Variables and `print()`

```python
a = 5
b = 1

print(a, b)
print(a)
print(1)
```

**Output:**

```text
5 1
5
1
```

**Explanation:**

- `a = 5` → Stores the value `5` in variable `a`.
- `b = 1` → Stores the value `1` in variable `b`.
- `print(a, b)` → Prints the values of both variables.
- `print(a)` → Prints the value stored in `a`.
- `print(1)` → Prints the number `1` directly.

# 2. `sep` and `end`

## A. `sep` — Separator

`sep` determines what appears between multiple values printed by the same `print()` statement.

```python
a = 5
b = 1

print(a, b, sep="*")
```

**Output:**

```text
5*1
```

Normally, `print(a, b)` displays `5 1` because the default separator is a space.

However, `sep="*"` replaces that space with `*`.

**Another example:**

```python
print(10, 20, 30, sep="-")
```

**Output:**

```text
10-20-30
```

## B. `end` — Ending

`end` determines what appears at the end of a `print()` statement.

```python
print(a, end=" Naba ")
print(b)
```

**Output:**

```text
5 Naba 1
```

**Why?**

- `print(a, end=" Naba ")` prints `5`, followed by ` Naba ` without moving to a new line.
- `print(b)` prints `1` on the same line and then moves to a new line.

Normally, `print()` automatically adds a newline at the end. The `end` parameter lets you change this behavior.

**Remember:**

- `sep` → What appears between values?
- `end` → What appears at the end of a print statement?

# 3. User Input — `input()`

The `input()` function takes data from the user.

```python
id = input("Id ")
```

**Example interaction:**

```text
Id 5
```

The program displays `Id ` and waits for the user to enter a value. The entered value is stored in the variable `id`.

## An Important Rule About `input()`

In Python, `input()` always returns a string (`str`), even when the user enters a number.

Consider this code:

```python
x = input("n1 : ")
y = input("n2 : ")

print(x + y)
```

**Input:**

```text
n1 : 10
n2 : 20
```

**Output:**

```text
1020
```

**Why does it not print `30`?**

Because `x` contains the string `"10"` and `y` contains the string `"20"`. When `+` is used with strings, it joins them together. This is called **concatenation**.

### String + String

```python
"10" + "20"
```

**Output:**

```text
1020
```

### Integer + Integer

```python
10 + 20
```

**Output:**

```text
30
```

## Why Do We Use `int()`?

The `int()` function converts a value into an integer.

```python
x = int(input("n1 : "))
y = int(input("n2 : "))

print(x + y)
```

**Input:**

```text
n1 : 10
n2 : 20
```

**Output:**

```text
30
```

Here, `int(input(...))` means: take the user's input and convert it into an integer.

# 3.1. Multiple User Input

Python allows us to take multiple inputs in a single line using `split()` and `map()`.

## A. Using `input().split()`

```python
x, y = input().split()

print(x)
print(y)
```

**Input:**

```text
10 20
```

**Output:**

```text
10
20
```

**Explanation:**

1. `input()` takes the entire line as a string.
2. `.split()` separates the input using spaces.
3. `x` stores `"10"` and `y` stores `"20"`.
4. Both values are strings (`str`), not integers.

## B. Using `map(int, input().split())`

```python
x, y = map(int, input().split())

print(x + y)
```

**Input:**

```text
10 20
```

**Output:**

```text
30
```

**Explanation:**

1. `input()` takes `10 20`.
2. `.split()` separates it into `"10"` and `"20"`.
3. `map(int, ...)` converts both strings into integers.
4. `x = 10` and `y = 20`.
5. `print(x + y)` prints `30`.

## C. Taking Three Inputs

```python
a, b, c = map(int, input().split())

print(a + b + c)
```

**Input:**

```text
10 20 30
```

**Output:**

```text
60
```

Here, three integers are taken in a single line and stored in three variables.

## D. Quick Comparison

| Code | Meaning |
|---|---|
| `input()` | Takes input as a string |
| `input().split()` | Separates multiple inputs into strings |
| `map(int, input().split())` | Separates multiple inputs and converts them into integers |
| `x, y = ...` | Stores two input values in two variables |
| `a, b, c = ...` | Stores three input values in three variables |

**Remember:** The number of input values must match the number of variables. For example, `x, y` expects two values.

# 4. `if-else`

We use `if-else` to check a condition and execute different code depending on whether the condition is true or false.

Your file contains this code:

```python
n, m = map(int, input().split())

if n > m:
    print(n)
else:
    print(m)
```

Suppose the input is:

```text
1 2
```

**Step by step:**

1. `input()` receives `"1 2"`.
2. `.split()` separates the values into `["1", "2"]`.
3. `map(int, ...)` converts both values into integers.
4. `n = 1` and `m = 2`.
5. The condition `n > m` checks whether `1 > 2`. It is false.
6. Therefore, the `else` block executes and prints `m`.

**Output:**

```text
2
```

**Main concept:** If the `if` condition is true, the `if` block executes. Otherwise, the `else` block executes.

# 5. `for` Loop and `range()`

A loop repeats a task multiple times.

Your file contains:

```python
for i in range(1, 19):
    if i % 2 != 0:
        print(i)
```

**Output:**

```text
1
3
5
7
9
11
13
15
17
```

Let's understand each part.

## A. `range(start, stop)`

```python
range(1, 19)
```

This generates numbers starting from `1` and stopping before `19`.

**Important:** The stop value is excluded.

Therefore, the numbers are `1, 2, 3, ..., 18`.

## B. `i % 2 != 0`

- `%` is the modulus operator. It gives the remainder after division.
- `i % 2` gives the remainder when `i` is divided by `2`.
- `!=` means not equal to.

An odd number leaves a remainder of `1` when divided by `2`.

| `i` | `i % 2` | `i % 2 != 0` | Printed? |
|---:|---:|---|---|
| 1 | 1 | True | Yes |
| 2 | 0 | False | No |
| 3 | 1 | True | Yes |
| 4 | 0 | False | No |
| 5 | 1 | True | Yes |

Therefore, only odd numbers are printed.

## C. `if i % 2:`

Your file also contains:

```python
for i in range(1, 20):
    if i % 2:
        print(i)
```

This produces the same output.

In Python, `0` is treated as false, while non-zero integers are treated as true. Therefore, `if i % 2:` also prints only odd numbers.

## D. `range(start, stop, step)`

Now let's use the `step` parameter.

```python
for i in range(1, 20, 2):
    print(i)
```

**Output:**

```text
1
3
5
7
9
11
13
15
17
19
```

Here:

- `start = 1` → Starts at `1`.
- `stop = 20` → Stops before `20`.
- `step = 2` → Increases by `2` each time.

Therefore, it prints `1, 3, 5, 7, ..., 19`.

### Reverse Loop

```python
for i in range(19, 1, -2):
    print(i)
```

**Output:**

```text
19
17
15
13
11
9
7
5
3
```

Here, `step = -2`, so the value decreases by `2` each time. The value `1` is not included because the loop stops before reaching the stop boundary.

| Topic | Meaning |
|---|---|
| `print()` | Displays output |
| `input()` | Takes input from the user |
| `int()` | Converts a value into an integer |
| `sep` | Defines the separator between printed values |
| `end` | Defines what appears at the end of a print statement |
| `input().split()` | Separates multiple inputs into strings |
| `map(int, input().split())` | Takes multiple inputs as integers |
| `if-else` | Checks a condition |
| `range(a, b)` | Generates numbers from `a` up to, but not including, `b` |
| `range(a, b, s)` | Generates numbers using step `s` |
| `%` | Calculates the remainder |
| `!=` | Means not equal to |

# Output Practice

**Code:**

```python
print(10, 20, sep="*")
print(30, end="!")
print(40)
```

**Output:**

```text
10*20
30!40
```

- `sep="*"` puts `*` between `10` and `20`.
- `print(10, 20, sep="*")` ends with a newline by default.
- `end="!"` makes the second `print()` end with `!` instead of a newline.
- `print(40)` prints `40` immediately after `30!`.
