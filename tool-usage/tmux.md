# Tmux

start new:

```text
tmux
```

start new with session name:

```text
tmux new -s myname
```

attach:

```text
tmux a  #  (or at, or attach)
```

attach to named:

```text
tmux a -t myname
```

list sessions:

```text
tmux ls
```

kill session:

```text
tmux kill-session -t myname
```

Kill all the tmux sessions:

```text
tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill
```

In tmux, hit the prefix `ctrl+b` \(my modified prefix is ctrl+a\) and then:

### List all shortcuts

to see all the shortcuts keys in tmux simply use the `bind-key ?` in my case that would be `CTRL-B ?`

### Sessions

```text
:new<CR>  new session
s  list sessions
$  name session
```

### Windows \(tabs\)

```text
c  create window
w  list windows
n  next window
p  previous window
f  find window
,  name window
&  kill window
```

### Panes \(splits\)

```text
%  vertical split
"  horizontal split

o  swap panes
q  show pane numbers
x  kill pane
+  break pane into window (e.g. to select text by mouse to copy)
-  restore pane from window
⍽  space - toggle between layouts
<prefix> q (Show pane numbers, when the numbers show up type the key to goto that pane)
<prefix> { (Move the current pane left)
<prefix> } (Move the current pane right)
<prefix> z toggle pane zoom
```

### Sync Panes

You can do this by switching to the appropriate window, typing your Tmux prefix \(commonly Ctrl-B or Ctrl-A\) and then a colon to bring up a Tmux command line, and typing:

```text
:setw synchronize-panes
```

