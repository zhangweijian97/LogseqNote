---
title: dice常用命令
---

## 授权
### kinit s2119299@INF.ED.AC.UK -r 7d -l 15h -f && aklog
## 激活环境
### source ~/miniconda3/etc/profile.d/conda.sh
### conda activate mlp
## 进入文件夹
### cd nlu/cw2/nlu_cw2/
## Jupyter Notebook
### nice -n 19 jupyter notebook --no-browser --port 23344
## longjob
### longjob -28day -nobackground -c "bash xxxx.sh"
### bash run_vgg_38_0_0.sh
## 转发
### lsof -ti:24641 | xargs kill -9
ssh -N -f -L localhost:24641:localhost:23344 s2119299@starship
## {{embed [[tmux常用命令]] }}
## {{embed [[conda常用命令]] }}
## {{embed [[GPU常用命令]] }}
## start JP 命令序列 例子 1
### kinit s2119299@INF.ED.AC.UK -r 7d -l 15h -f && aklog
{WAIT:100}ZWJ@dice
{WAIT:100}ssh starship
{WAIT:1000}tmux
{WAIT:100}kinit s2119299@INF.ED.AC.UK -r 7d -l 15h -f && aklog
{WAIT:100}ZWJ@dice
{WAIT:100}source ~/miniconda3/etc/profile.d/conda.sh
{WAIT:100}conda activate nlu
{WAIT:100}cd ~
{WAIT:100}nice -n 19 jupyter notebook --no-browser --port 23344
## afs 地址
### /afs/inf.ed.ac.uk/user/s21/s2119299/
