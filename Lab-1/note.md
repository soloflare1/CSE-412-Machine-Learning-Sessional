 # Topic - `print()`, `sep`, `end`, `input()`, `int()`, `if-else`, and `for loops`.

# 1. Variables and `print()`

```
a = 5b = 1print(a, b)print(a)print(1)
```

Explanation:

- `a = 5` → Stores the value `5` in variable `a`.
- `b = 1` → Stores the value `1` in variable `b`.
- `print(a, b)` → Prints the values of both variables.

Output:

```
5 1
5
1
```

`print(a)` displays the value stored in `a`, while `print(1)` directly displays the number `1`.

# 2. `sep` and `end`

## A. `sep` — Separator

`sep` determines what appears between multiple values printed by the same `print()` statement.

```
a = 5b = 1print(a, b, sep="*")
```

Output:

```
5*1
```

Normally, `print(a, b)` displays `5 1` because the default separator is a space.

However, `sep="*"` replaces that space with `*`.

Another example:

```
print(10, 20, 30, sep="-")
```

Output:

```
10-20-30
```

## B. `end` — Ending

`end` determines what appears at the end of a `print()` statement.

```
print(a, end=" Naba ")print(b)
```

Output:

```
5 Naba 1
```

Why?

- `print(a, end=" Naba ")` prints `5`, followed by `Naba` without moving to a new line.
- `print(b)` prints `1` on the same line and then moves to a new line.

Normally, `print()` automatically adds a newline at the end. The `end` parameter lets you change this behavior.

Remember:

- `sep` → What appears between values?
- `end` → What appears at the end of a print statement?

# 3. User Input — `input()`

The `input()` function takes data from the user.

```
id = input("Id ")
```

Example interaction:

```
Id 5
```

The program displays `Id ` and waits for the user to enter a value. The entered value is stored in the variable `id`.

## An important rule about `input()`

In Python, `input()` always returns a string (`str`), even when the user enters a number.

Consider this code:

```
x = input("n1 : ")y = input("n2 : ")print(x + y)
```

Input:

```
n1 : 10
n2 : 20
```

Output:

```
1020
```

Why does it not print `30`?

Because `x` contains the string `"10"` and `y` contains the string `"20"`. When `+` is used with strings, it joins them together. This is called concatenation.

String + String

`"10" + "20"`

## `"1020"`

Integer + Integer

`10 + 20`

## `30`

## Why do we use `int()`?

The `int()` function converts a value into an integer.

```
x = int(input("n1 : "))y = int(input("n2 : "))print(x + y)
```

Input:

```
n1 : 10
n2 : 20
```

Output:

```
30
```

Here, `int(input(...))` means: take the user's input and convert it into an integer.

# 4. `if-else`

We use `if-else` to check a condition and execute different code depending on whether the condition is true or false.

Your file contains this code:

```
n, m = map(int, input().split())if n > m:    print(n)else:    print(m)
```

Suppose the input is:

```
1 2
```

Step by step:

1. `input()` receives `"1 2"`.
2. `.split()` separates the values into `["1", "2"]`.
3. `map(int, ...)` converts both values into integers.
4. `n = 1` and `m = 2`.
5. The condition `n > m` checks whether `1 > 2`. It is false.
6. Therefore, the `else` block executes and prints `m`.

Output:

```
2
```

Main concept: If the `if` condition is true, the `if` block executes. Otherwise, the `else` block executes.

# 5. `for` loop and `range()`

A loop repeats a task multiple times.

Your file contains:

```
for i in range(1, 19):    if i % 2 != 0:        print(i)
```

Output:

```
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

```
range(1, 19)
```

This generates numbers starting from `1` and stopping before `19`.

Important: The stop value is excluded.

Therefore, the numbers are `1, 2, 3, ..., 18`.

## B. `i % 2 != 0`

- `%` is the modulus operator. It gives the remainder after division.
- `i % 2` gives the remainder when `i` is divided by `2`.
- `!=` means not equal to.

An odd number leaves a remainder of `1` when divided by `2`.

| `i` | `i % 2` | `i % 2 != 0` | Printed? |
| --- | ------- | ------------ | -------- |
| 1   | 1       | True         | Yes      |
| 2   | 0       | False        | No       |
| 3   | 1       | True         | Yes      |
| 4   | 0       | False        | No       |
| 5   | 1       | True         | Yes      |

Therefore, only odd numbers are printed.

## C. `if i % 2:`

Your file also contains:

```
for i in range(1, 20):    if i % 2:        print(i)
```

This produces the same output.

In Python, `0` is treated as false, while non-zero integers are treated as true. Therefore, `if i % 2:` also prints only odd numbers.

## D. `range(start, stop, step)`

Now let's use the `step` parameter.

```
for i in range(1, 20, 2):    print(i)
```

Output:

```
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

### Reverse loop

```
for i in range(19, 1, -2):    print(i)
```

Output:

```
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

# Quick revision for your lab exam

| Topic            | Meaning                                                  |
| ---------------- | -------------------------------------------------------- |
| `print()`        | Displays output                                          |
| `input()`        | Takes input from the user                                |
| `int()`          | Converts a value into an integer                         |
| `sep`            | Defines the separator between printed values             |
| `end`            | Defines what appears at the end of a print statement     |
| `if-else`        | Checks a condition                                       |
| `range(a, b)`    | Generates numbers from `a` up to, but not including, `b` |
| `range(a, b, s)` | Generates numbers using step `s`                         |
| `%`              | Calculates the remainder                                 |
| `!=`             | Means not equal to                                       |

output?

```
* print(10, 20, sep="*")
* print(30, end="!")
* print(40)
```
`10*20`, then `30!40` on the same line
