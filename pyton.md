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

### код для машины на python (я старался!)
```
print((' ' * 6) + ('*' * 9))
print((' ' * 5) + ('*') + (' ' * 9) + ('*'))
print((' ' * 1) + ('*' * 4) + (' ' * 11) + ('*' * 5))
print((' ' * 1) + ('*' ) + (' ' * 2) +(' ' * 3 ) + (' ' * 8) + (' ' * 3 ) + (' ' * 2) + ('*' ))
print((' ' * 1) + ('*' * 3) + (' ' * 3) + ('*' * 8) + (' ' * 3) + ('*' * 3))
print((' ' * 3) + ('*' ) + (' ' * 3) + ('*' ) + (' ' * 6) + ('*' ) + (' ' * 3) + ('*' ))
print((' ' * 4) + ('*' * 3) + (' ' * 8) + ('*' * 3))
```

### код для написания редактора на python
```python
from tkinter import *
import ctypes
import re
import os



def exeute(event=None):
    with open('run.py', 'w', encoding='utf-8') as f:
        f.write(editArea.get('1.0', END))

    os.system('start cmd /K "python run.py')


def changes(event=None):
    global previousText

    if editArea.get('1.0', END) == previousText:
        return
    
    for tag in editArea.tag_names():
        editArea.tag_remove(tag, '1.0', END)

    i = 0
    for pattern, color in repl:
        for start, end in search_re(pattern, editArea.get('1.0',END)):
            editArea.tag_add(f'{i}', start, end) 
            editArea.tag_config(f'{i}', foreground=color) 

            i += 1

    previousText = editArea.get('1.0', END)  


def search_re(pattern, text):
    matches = []
    text = text.splitlines()

    for i, line in enumerate(text):
        for match in re.finditer(pattern, line):
            matches.append((f"{i + 1}.{match.start()}", f"{i + 1}.{match.end()}" ))
        return matches




def rgb(rgb):
    return "#%02x%02x%02x" % rgb

ctypes.windll.shcore.SetProcessDpiAwareness(True)


root = Tk()
root.geometry('700x500')
root.title('Редактор кода')
previousText = ''

normal = rgb((234, 234, 234))
keywords = rgb((234, 95, 95))
comments = rgb((95, 234, 156))
string = rgb((234, 162, 95))
function = rgb((95, 211, 234))
background = rgb((42, 42, 42))
font = 'consolas 15'

repl = [
         ['(^| )(False|None|True|and|as|assert|asyns|await|break|class|continue|def|del|elif|else|except|finally|for|from|global|if|import|in|is|lambda|nonlocal|not|or|pass|raise|return|tru|while|with|yield)($| )', keywords],
         ['".*?"', string],
         ['\".*?\"', string],
         ['#.*?$', comments],
]

editArea = Text(
    root, background=background, foreground=normal, insertbackground=normal, relief=FLAT, border=30, font=font
)

editArea.pack(fill=BOTH, expand=1)

editArea.insert('1.0', '')

editArea.bind('<KeyRelease>', changes)

root.bind('<Control-r>', exeute)

changes()

root.mainloop()
```
