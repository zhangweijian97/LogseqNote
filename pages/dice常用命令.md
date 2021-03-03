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
## {{embed [[tmux常用命令]] }}
## {{embed [[conda常用命令]] }}
## {{embed [[GPU常用命令]] }}
##
