+++
date = "2018-12-28T16:24:01+08:00"
title =  "Several shell skills"
+++
# Awk related 

- 在 awk 中使用 shell变量: 设置 awk 变量传导
```shell
a=1
echo $a
awk -v b="$a" 'BEGIN {print b}'
```
