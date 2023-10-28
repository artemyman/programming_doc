# Pyton

### код для калькулятора на python:

```python
while True: print(eval(input('>>>')))
```

### код для написание своего списка(на Python):

```python
n = int(input("Enter length"))

user_list = []
i = 0
while i < n:
    string = "Enter element #" + str(i + 1) + ": "
    user_list.append(input(string))
    i += 1

print(user_list)
```

### код для ёлки на Python:

```python
n = int(input("высота ёлки: "))

current = 1
maxLen = 2 * n - 1

while current <= n:
    starCount = 2 * current - 1
    spaceCount = int((maxLen - starCount)/2)
    print((' ' * spaceCount) + ('*' * starCount))
    current += 1


legCount = int(n/10) + 1
spaceCount = int((maxLen - 1)/2)

while legCount > 0:
    print((' ' * spaceCount) + '*')
    legCount -= 1
```
