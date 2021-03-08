---
title: ffmpeg常用命令
---

## 剪辑
### ffmpeg -ss 00:00:00 -t 00:01:00 -i vogue.mp3 -vcodec copy -acodec copy final.mp3
## 压缩
### ffmpeg -i input.mpg -b:v 2048k -s 1920x1080 output.mp4
