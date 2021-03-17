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
## 两个根目录
### /home/s2119299
### /exports/eddie/scratch/s2119299
## 命令
### 传输文件，用scp或者rsync
#### scp -r data/ s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
#### rsync -r data/ s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
#### scp -r testuploadtoeddie.txt s2119299@eddie.ecdf.ed.ac.uk:/exports/eddie/scratch/s2119299/
#### scp -r testuploadtoeddie.txt s2119299@eddie.ecdf.ed.ac.uk:/home/s2119299/
