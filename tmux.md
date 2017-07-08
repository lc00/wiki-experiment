Session (theme) > Window (project) > Pane (view)

*List sessions*
tmux ls
ctrl + b, s

*Add session*
tmux new -s session-name

*Attach to an existing session*
tmux a
tmux a -t session-name

*Detach from session*
tmux detach
ctrl + b, d

*Kill a session*
tmux kill-session -t session-name

*Kill a window*
tmux kill-window -t window-name

*Navigate panes*
select-pane -D/-U/-L/-R

*Ctrl + b Reference*

(mapped mine to Ctrl + space)

c - new window
w - list windows
n - next window
p - previous window
0-9 - window 0-9
& - kill window

% - horizontal pane (mapped mine to -)
“ - vertical pane (mapped mine to |)
q - show pane numbers
o - toggle panes
; - return to last pane
x - kill pane
