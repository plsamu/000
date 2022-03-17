# Open VScode from shift + right click

{% embed url="https://quickfever.com/enable-open-command-window-here-option-shift-right-click-menu-windows-10" %}

```
start > search > regedit
```

Go to:

```
HKEY_CLASSES_ROOT\Directory\Background\shell\
or
HKEY_CLASSES_ROOT\Directory\shell\
or
HKEY_CLASSES_ROOT\Drive\shell\
```

#### WIP - now create in desktop your own .reg file

```
add_vscode.reg
```

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode]
@="Open VSCode Here"
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode\command]
@="code ."
```
