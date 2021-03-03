---
title: dice常用命令
---

## 激活环境
### kinit s2119299@INF.ED.AC.UK -r 7d -l 15h -f && aklog
### source ~/miniconda3/etc/profile.d/conda.sh
### conda activate mlp
### cd nlu/cw2/nlu_cw2/
### nice -n 19 jupyter notebook --no-browser --port 23344
## longjob
### longjob -28day -nobackground -c "bash xxxx.sh"
### bash run_vgg_38_0_0.sh
## nice -n 19 jupyter notebook --no-browser --port 23344
## {{embed [[tmux常用命令]] }}
## {{embed [[conda 常用命令]] }}
## pytorch 显卡
### import torch
### print(torch.__version__)
### print(torch.version.cuda)
### print(torch.backends.cudnn.version())
##
