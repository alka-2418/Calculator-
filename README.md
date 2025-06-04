import tkinter as tk
from tkinter import messagebox

# Function to evaluate the expression
def calculate():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(tk.END, str(result))
    except ZeroDivisionError:
        messagebox.showerror("Math Error", "Cannot divide by zero!")
        entry.delete(0, tk.END)
    except Exception:
        messagebox.showerror("Input Error", "Invalid expression!")
        entry.delete(0, tk.END)

# Function to update entry with button press
def press(key):
    entry.insert(tk.END, key)

# Function to clear entry
def clear():
    entry.delete(0, tk.END)

# Main window
root = tk.Tk()
root.title("Basic Calculator")
root.geometry("320x420")
root.configure(bg="#f0f0f0")
root.resizable(False, False)

# Entry widget
entry = tk.Entry(root, font=("Arial", 22), bd=5, relief="ridge", justify="right")
entry.pack(fill="x", padx=10, pady=15, ipady=10)

# Button layout
button_texts = [
    ['7', '8', '9', '/'],
    ['4', '5', '6', '*'],
    ['1', '2', '3', '-'],
    ['0', '.', '=', '+']
]

# Create buttons
for row_values in button_texts:
    row_frame = tk.Frame(root, bg="#f0f0f0")
    row_frame.pack(expand=True, fill="both", padx=10, pady=2)
    for value in row_values:
        if value == '=':
            btn = tk.Button(row_frame, text=value, font=("Arial", 18, "bold"),
                            bg="#4CAF50", fg="white", command=calculate)
        else:
            btn = tk.Button(row_frame, text=value, font=("Arial", 18),
                            command=lambda x=value: press(x))
        btn.pack(side="left", expand=True, fill="both", padx=2, pady=2)

# Clear button
clear_btn = tk.Button(root, text="Clear", font=("Arial", 16, "bold"),
                      bg="#f44336", fg="white", command=clear)
clear_btn.pack(fill="x", padx=10, pady=10)

# Start application
root.mainloop()# Calculator-
Calculator using python 
