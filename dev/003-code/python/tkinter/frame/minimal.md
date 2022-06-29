# Minimal

```python
# main.py

import tkinter as tk
from tkinter import END, LEFT, ttk

root = tk.Tk()
root.tk.call('lappend', 'auto_path', './awthemes-10.4.0')
root.tk.call('package', 'require', 'awdark')
style = ttk.Style()  # create a style
style.theme_use('awdark')  # set the theme
root.geometry("200x400")

container = ttk.Frame(root)
container.pack(side="top", fill="both", expand=True)

ttk.Button(container, text="B1", takefocus=0).grid(
    row=0, column=0, sticky="nw")

ttk.Button(container, text="B2", takefocus=0).grid(
    row=1, column=0, sticky="nw")

root.mainloop()
```
