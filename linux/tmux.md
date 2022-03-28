# Tmux

{% embed url="https://tmuxcheatsheet.com" %}

### Sessions

```
tmux ls
tmux kill-ses -t mysession
tmux new -s mysession            # create and attach
tmux new -ds mysession           # guess
tmux a -t my                     # attach to mysession
```

### CTRL + B

```
ctrlb then (->) shift + 5 (%)         # split vertically
ctrlb -> shift + 2 (")                # split horizontally
ctrlb -> x                            # close pane
```
