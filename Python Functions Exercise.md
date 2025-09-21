# Python Functions Exercise
## 1. Functions in Python
Functions execute tasks multiple times. The user invokes the function by providing inputs to it (known as arguments), and the function simply executes these instructions internally (as if it were a black box). This exercise will have you experience arguments, variable scope, and troubleshooting.
## 1a. Unit Conversion Program (kpl ↔ mpg)
```python
def kpl_to_mpg(*kpl_values):
    conversion_factor = 2.35215  # 1 kpl = 2.35215 mpg
    mpg_values = []
    for kpl in kpl_values:
        try:
            kpl = float(kpl)
            mpg = kpl * conversion_factor
            mpg_values.append(mpg)
        except ValueError:
            print(f"Invalid input: {kpl}. Please enter numbers only.")
    return mpg_values

def mpg_to_kpl(*mpg_values):
    conversion_factor = 1 / 2.35215
    kpl_values = []
    for mpg in mpg_values:
        try:
            mpg = float(mpg)
            kpl = mpg * conversion_factor
            kpl_values.append(kpl)
        except ValueError:
            print(f"Invalid input: {mpg}. Please enter numbers only.")
    return kpl_values

# User interaction
choice = input("Convert from (1) kpl to mpg or (2) mpg to kpl? Enter 1 or 2: ")
values = input("Enter values separated by spaces: ").split()

if choice == "1":
    result = kpl_to_mpg(*values)
    print("Converted to mpg:", result)
elif choice == "2":
    result = mpg_to_kpl(*values)
    print("Converted to kpl:", result)
else:
    print("Invalid choice. Please enter 1 or 2.")
```
### 1b. Function with any number of unnamed arguments in reverse order
```python
def print_reverse(*args):
    for value in reversed(args):
        print(value)

# Example
print_reverse(1, 2, 3, 4)
```
### 1c. Effects of modifying lists or dictionaries in functions
#### Unsafe modification (affects original)
```python
def modify_list(lst):
    lst.append(4)  # Changes original list

my_list = [1, 2, 3]
modify_list(my_list)
print(my_list)  # Output: [1, 2, 3, 4]
```

















#### Safe modification using .copy()
```python
def modify_list_safe(lst):
    lst_copy = lst.copy()  # Work with a copy
    lst_copy.append(100)
    print("Inside function:", lst_copy)

my_list = [1, 2, 3]
modify_list_safe(my_list)
print("Outside function:", my_list)  # Original list unchanged
```
#### Dictionary example
```python
def modify_dict_safe(d):
    d_copy = d.copy()
    d_copy["new_key"] = "new_value"
    print("Inside function:", d_copy)

my_dict = {"a": 1, "b": 2}
modify_dict_safe(my_dict)
print("Outside function:", my_dict)  # Original dict unchanged
```
### 1d. Global vs local variable behavior
```python
def my_func(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

my_func(1, 2, 3, 4, 5, 6)
x = 5

def funct_1():
    x = 3  # Local variable, does not affect global x

def funct_2():
    global x
    x = 2  # Modifies global x

funct_1()
print(x)  # Output: 5
funct_2()
print(x)  # Output: 2
```
### 2. Troubleshooting
#### 2a. Correct my_func to accept multiple unnamed arguments
```python
def my_func(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

my_func(1, 2, 3, 4, 5, 6)
```
### 2b. Why x prints 10 instead of 100
```python
def my_func_global():
    x = 100  # Local variable, does not affect global x

x = 10
my_func_global()
print(x)  # Output: 10
```
#### Fix using global:
```python
def my_func_global():
    global x
    x = 100

x = 10
my_func_global()
print(x)  # Output: 100
```
# Challenges
-Comprehending local versus global variables.

-Managing multiple arguments in functions and checking user input.

-Preventing unintended modifications to lists/dictionaries by invoking .copy(). 





























