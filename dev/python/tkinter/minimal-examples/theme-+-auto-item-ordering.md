# Theme + auto item ordering

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
container.columnconfigure(tuple(range(60)), weight=1)
container.rowconfigure(tuple(range(30)), weight=1)

listbox = tk.Listbox(container)

btn1 = ttk.Button(container, text="B1", takefocus=0)
btn1.configure(command=lambda: {print('ciaoo')})

btn2 = ttk.Button(container, text="B2", takefocus=0)
btn2.configure(command=lambda: {print('wooo')})

objs = [listbox, btn1, btn2]

counter = 0
for obj in objs:
    obj.grid(column=0, row=counter, sticky="news")
    counter += 1

root.mainloop()
```
