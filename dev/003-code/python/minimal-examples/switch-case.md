# Switch Case

```python
import platform
import os

osname = os.name
platform = platform.system()

match platform:
    case "Linux":
        command = "python3 --version"
        os.system("gnome-terminal -e 'bash -c \""+command+";bash\"'")
    case "Darwin":
        pass
    case "Windows":
        pass
    case _: pass
```
