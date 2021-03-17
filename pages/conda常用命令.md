---
title: conda常用命令
---

## conda remove -n your_env_name(虚拟环境名称) --all
## conda info --env
## conda create -n your_env_name python
## conda activate
## conda deactivate
## conda intall
## 从requirements.txt安装
### conda install --yes --file requirements.txt
### $ while read requirement; do conda install --yes $requirement; done < requirements.txt
### $ while read requirement; do conda install --yes $requirement || pip install $requirement; done < requirements.txt
###
