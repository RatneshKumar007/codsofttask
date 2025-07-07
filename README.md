import tkinter as tk
from tkinter import messagebox

# Function to add task
def add_task():
    task = entry.get()
    if task != "":
        listbox.insert(tk.END, task)
        entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Input Error", "Please enter a task.")

# Function to delete selected task
def delete_task():
    try:
        selected_index = listbox.curselection()
        listbox.delete(selected_index)
    except:
        messagebox.showwarning("Selection Error", "Please select a task to delete.")

# Function to clear all tasks
def clear_tasks():
    confirm = messagebox.askyesno("Clear All", "Are you sure you want to clear all tasks?")
    if confirm:
        listbox.delete(0, tk.END)

# Main GUI window
root = tk.Tk()
root.title("To-Do List")
root.geometry("400x450")
root.config(bg="#f0f0f0")

# Title label
tk.Label(root, text="To-Do List", font=("Helvetica", 18, "bold"), bg="#f0f0f0").pack(pady=10)

# Entry box
entry = tk.Entry(root, font=("Helvetica", 14))
entry.pack(pady=10, padx=20, fill=tk.X)

# Listbox to display tasks
listbox = tk.Listbox(root, font=("Helvetica", 14), height=10, selectbackground="#a0a0a0")
listbox.pack(pady=10, padx=20, fill=tk.BOTH)

# Button frame
button_frame = tk.Frame(root, bg="#f0f0f0")
button_frame.pack(pady=10)

# Buttons
tk.Button(button_frame, text="Add Task", width=12, command=add_task).grid(row=0, column=0, padx=5)
tk.Button(button_frame, text="Delete Task", width=12, command=delete_task).grid(row=0, column=1, padx=5)
tk.Button(button_frame, text="Clear All", width=12, command=clear_tasks).grid(row=0, column=2, padx=5)

# Run app
root.mainloop()
