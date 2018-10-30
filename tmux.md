# Basic commands

```zsh

# new session
tmux new
tmux new -s [name of session]
tmux new -s foo

# tmux command prompt
ctrl+b :

# new session while attached
ctrl+b :new<enter>

# name session while attached
ctrl+b $

# kill session
tmux kill-session -t foo

# exit
exit

# detach
ctrl+b d

# list sessions
tmux ls
# while attached
ctrl+b s  list sessions

# attach to a session
tmux attach-session -t 0
tmux attach-session -t foo
tmux a -t [name of session]

# attach to most recently created session
tmux a #

# split pane horizontally
ctrl+b "

# split pane vertically
ctrl+b %

# move from pane to pane
ctrl+b [arrow key]

# resizing
ctrl+b :
resize-pane -U
resize-pane -D 1
resize-pane -L 2
resize-pane -R 3

# kill pane
ctrl+b x

# kill tmux server, along with all sessions
tmux kill-server

```

# Customization

.tmux.conf file

# References

https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340

https://gist.github.com/MohamedAlaa/2961058
