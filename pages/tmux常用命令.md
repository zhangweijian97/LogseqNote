---
title: tmux常用命令
---

## tmux 创建新会话
### tmux new -s dome
## tmux detach 断开会话
### command+b，d 退出当前 Tmux 窗口，但是会话和里面的进程仍然在后台运行
## tmux a 重新接入会话
### tmux a -t demo
## tmux attach -t 0
## tmux ls
## tmux kill-session -t 0
## tmux switch -t 0
