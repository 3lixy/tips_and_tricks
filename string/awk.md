#AWK

##### print all columns from x onwards (example is from column 8)
```
awk '{ s = ""; for (i = 8; i <= NF; i++) s = s $i " "; print s }'
```