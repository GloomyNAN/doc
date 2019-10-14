---
title: Software
---

find 
gerp
ps
top
iconv
awke

批量编码转化

```shell
find *.PHP -exec sh -c "iconv -f GBK -t UTF8 {} > {}.php" \;  

find  ./ -name  "*.c" -exec sh -c "iconv -f GB18030 -t UTF8 {} > {}.c" \;

rm -rf *.c
rename 's/\.xml$//' *.xml
```
Aria2GUI


