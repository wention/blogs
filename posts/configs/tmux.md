TMUX 常用配置
============

## 参考配置1
```
# -- general -------------------------------------------------------------------
set -g prefix2 C-a
set-option -g history-limit 10000
setw -q -g utf8 on

# -- display -------------------------------------------------------------------
set -g base-index 1           # start windows numbering at 1
setw -g pane-base-index 1     # make pane numbering consistent with windows

setw -g automatic-rename on   # rename window to reflect current program
set -g renumber-windows on    # renumber windows when a window is closed
set -g set-titles on          # set terminal title
	
# clear both screen and history
bind -n C-l send-keys C-l \; run 'sleep 0.2' \; clear-history

# -- navigation ----------------------------------------------------------------
# pane navigation
bind -r h select-pane -L  # move left
bind -r j select-pane -D  # move down
bind -r k select-pane -U  # move up
bind -r l select-pane -R  # move right
bind > swap-pane -D       # swap current pane with the next one
bind < swap-pane -U       # swap current pane with the previous one

# pane resizing
bind -r H resize-pane -L 2
bind -r J resize-pane -D 2
bind -r K resize-pane -U 2
bind -r L resize-pane -R 2

# window navigation
unbind n
unbind p
bind -r C-h previous-window # select previous window
bind -r C-l next-window     # select next window
bind Tab last-window        # move to last active window

# -- user customizations -------------------------------------------------------
# force Vi mode
set -g status-keys vi
set -g mode-keys vi
```
