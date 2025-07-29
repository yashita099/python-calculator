from tkinter import *
from math import factorial
from sympy import sympify # type: ignore

root = Tk()
root.title('DataFlair - Calculator')
root.geometry("400x550")  # Increase window size

i = 0

def get_variables(num):
    global i
    display.insert(i, num)
    i += 1

def calculate():
    entire_string = display.get()
    try:
        result = sympify(entire_string)
        clear_all()
        display.insert(0, result)
    except Exception:
        clear_all()
        display.insert(0, "Error")

def get_operation(operator):
    global i
    length = len(operator)
    display.insert(i, operator)
    i += length

def clear_all():
    display.delete(0, END)

def undo():
    entire_string = display.get()
    if len(entire_string):
        new_string = entire_string[:-1]
        clear_all()
        display.insert(0, new_string)
    else:
        clear_all()
        display.insert(0, "Error")

def fact():
    entire_string = display.get()
    try:
        result = factorial(int(entire_string))
        clear_all()
        display.insert(0, result)
    except Exception:
        clear_all()
        display.insert(0, "Error")

# Input display with larger font
display = Entry(root, font=("Arial", 24))
display.grid(row=1, columnspan=6, sticky=N+E+W+S, pady=10)

# Reusable button creator with larger font and padding
def create_button(text, row, col, cmd):
    Button(root, text=text, font=("Arial", 18), command=cmd).grid(row=row, column=col, sticky=N+S+E+W, padx=3, pady=3)

# Buttons layout
buttons = [
    ("1", 2, 0, lambda: get_variables(1)),
    ("2", 2, 1, lambda: get_variables(2)),
    ("3", 2, 2, lambda: get_variables(3)),
    ("4", 3, 0, lambda: get_variables(4)),
    ("5", 3, 1, lambda: get_variables(5)),
    ("6", 3, 2, lambda: get_variables(6)),
    ("7", 4, 0, lambda: get_variables(7)),
    ("8", 4, 1, lambda: get_variables(8)),
    ("9", 4, 2, lambda: get_variables(9)),
    ("AC", 5, 0, clear_all),
    ("0", 5, 1, lambda: get_variables(0)),
    (".", 5, 2, lambda: get_variables(".")),
    ("+", 2, 3, lambda: get_operation("+")),
    ("-", 3, 3, lambda: get_operation("-")),
    ("*", 4, 3, lambda: get_operation("*")),
    ("/", 5, 3, lambda: get_operation("/")),
    ("pi", 2, 4, lambda: get_operation("*3.14")),
    ("%", 3, 4, lambda: get_operation("%")),
    ("(", 4, 4, lambda: get_operation("(")),
    ("exp", 5, 4, lambda: get_operation("**")),
    ("<-", 2, 5, undo),
    ("x!", 3, 5, fact),
    (")", 4, 5, lambda: get_operation(")")),
    ("^2", 5, 5, lambda: get_operation("**2")),
]

for (text, row, col, cmd) in buttons:
    create_button(text, row, col, cmd)

# Equal button spanning full width
Button(root, text="=", font=("Arial", 18), command=calculate).grid(row=6, column=0, columnspan=6, sticky=N+S+E+W, padx=3, pady=10)

root.mainloop()
