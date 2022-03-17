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

#### now create in desktop your own .reg file

```
add_vscode.reg
```

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode]
@="Open VSCode Here"
"Extended"=""

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode\command]
@="powershell start-process 'code.cmd' ' .' -WindowStyle Hidden"
```

#### double click to add the new option

## Tried

```
powershell -?
```

```batch
C:\WINDOWS\system32\cmd.exe /k start "" "code.cmd . "
```

```scss
powershell.exe -windowstyle hidden { Start-Process -WindowStyle Hidden code.cmd -ArgumentList "." }
```

## Raw

{% embed url="https://stackoverflow.com/questions/36442020/windowstyle-hidden-not-working-on-powershell" %}

{% embed url="https://superuser.com/questions/413939/how-to-start-a-program-with-command-line-arguments-on-windows-cmd-with-start" %}
