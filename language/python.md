# TEXT

##### Python 2.4+,3.x portable excepton handling
```
import sys
try:
    ...
except Exception:
    t, e = sys.exc_info()[:2]
    print(e)
```