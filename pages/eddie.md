---
title: Eddie
---

## 相关资源
### [Who can use Eddie](https://www.wiki.ed.ac.uk/display/ResearchServices/Who+can+use+Eddie)
### [Eddie Quickstart CheatSheet](https://www.wiki.ed.ac.uk/display/PPE/Eddie+Quickstart+CheatSheet)
### [How to use the Eddie computer cluster](https://www.wiki.ed.ac.uk/display/sbsdocs/How+to+use+the+Eddie+computer+cluster)
#### Log in to eddie3 from macOS
### [Create Group](https://www.wiki.ed.ac.uk/display/ServiceDelivery/Create+Group)
### [Introduction to Eddie](https://www.wiki.ed.ac.uk/display/ResearchServices/Introduction+to+Eddie)
### [Example Staging Scripts](https://www.wiki.ed.ac.uk/display/ResearchServices/Example+Staging+Scripts)
### [Job Submission](https://www.wiki.ed.ac.uk/display/ResearchServices/Job+Submission)
## 两个根目录
### /home/s2119299
#### 用cd 回到的是这一个
### /exports/eddie/scratch/s2119299
## 命令
### 传输文件，用scp或者rsync
#### scp -r data/ s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
#### scp -r data/ s2119299@eddie.ecdf.ed.ac.uk:/home/s2119299/
#### rsync -r data/ s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
#### rsync -r data/ s2119299@eddie.ecdf.ed.ac.uk:/home/s2119299/
### 传输文件夹，加一个 -r
### 草稿
#### scp -r data/ s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
## 询问IS helpline，group space
### 编号 I210317-1573
## 配置环境
### Anaconda
### 更改envs和pkgs路径
## 命令例子
### 
#+BEGIN_SRC python
#!/bin/sh
# Grid Engine options (lines prefixed with #$)
#$ -N pretrain_fac_adapter              
#$ -cwd                  
#$ -l h_rt=10:00:00 
#$ -l h_vmem=32G
#  These options are:
#  job name: -N
#  use the current working directory: -cwd
#  runtime limit of 5 minutes: -l h_rt
#  memory limit of 1 Gbyte: -l h_vmem

# Initialise the environment modules
. /etc/profile.d/modules.sh

# Request GPUs: 
#$ -pe gpu-titanx 4

# Load Python
module load anaconda
source activate kadapter

# Run the program
bash ./run_pretrain_fac-adapter.sh
#+END_SRC
