# Python MCQs (Intermediate Level)

## 1. Functions + Mutable Default Argument

```python
def add_item(item, lst=[]):
    lst.append(item)
    return lst

print(add_item(1))
print(add_item(2))
```

What is the output?

- **A.** `[1]` and `[2]`
- **B.** `[1]` and `[1, 2]`
- **C.** `[1, 2]` and `[1, 2]`
- **D.** Error

## 2. Dictionary Comprehension

```python
nums = [1, 2, 3, 4]

result = {x: x**2 for x in nums if x % 2 == 0}

print(sum(result.values()))
```

What is printed?

- **A.** 10
- **B.** 16
- **C.** 20
- **D.** 25

## 3. Set Operations

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(len(a ^ b))
```

What is the output?

- **A.** 2
- **B.** 4
- **C.** 6
- **D.** 8

## 4. Nested Function Scope

```python
x = 10

def outer():
    x = 20
    
    def inner():
        return x + 5
    
    return inner()

print(outer())
```

What is printed?

- **A.** 10
- **B.** 15
- **C.** 20
- **D.** 25

## 5. Tuple and List Mutation

```python
t = ([1, 2], [3, 4])

t[0].append(5)

print(len(t[0]) + len(t[1]))
```

- **A.** 4
- **B.** 5
- **C.** 6
- **D.** Error

## 6. Function Returning Multiple Values

```python
def calc(a, b):
    return a+b, a*b

x, y = calc(2, 5)

print(x + y)
```

- **A.** 7
- **B.** 10
- **C.** 17
- **D.** 20

## 7. List Slicing Calculation

```python
nums = [2, 4, 6, 8, 10]

print(sum(nums[1:4]))
```

- **A.** 12
- **B.** 18
- **C.** 24
- **D.** 28

## 8. Dictionary Update Logic

```python
data = {'a': 1, 'b': 2}

data['a'] += data['b']
data['b'] += data['a']

print(data['a'] + data['b'])
```

- **A.** 5
- **B.** 6
- **C.** 7
- **D.** 8

## 9. Lambda with Sorted

```python
items = [(1, 3), (2, 1), (4, 2)]

items.sort(key=lambda x: x[1])

print(items[0][0] + items[-1][1])
```

- **A.** 3
- **B.** 4
- **C.** 5
- **D.** 6

## 10. Combining Collections

```python
nums = [1, 2, 2, 3, 4, 4]

unique = set(nums)

result = {x: x*2 for x in unique}

print(sum(result.values()))
```

- **A.** 10
- **B.** 16
- **C.** 20
- **D.** 24

## Answers

| Question | Answer |
|----------|--------|
| 1        | B      |
| 2        | C      |
| 3        | B      |
| 4        | D      |
| 5        | B      |
| 6        | C      |
| 7        | B      |
| 8        | D      |
| 9        | C      |
| 10       | C      |
