---
title: GPU常用命令
---

- lspci | grep -i nvidia
- nvidia-smi
	- watch -n 10 nvidia-smi
- 和 pytorch
	- import torch
	- print(torch.__version__)
	- print(torch.version.cuda)
	- print(torch.backends.cudnn.version())
	- torch.cuda.is_available()
	- torch.cuda.device_count()
	- torch.cuda.get_device_name(0)
	- torch.cuda.current_device()