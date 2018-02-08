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
##### List all releases for pypi package

https://pypi.python.org/simple/<package_name>/

##### install setuptools for python 2.4.3

wget https://pypi.python.org/packages/61/3c/8d680267eda244ad6391fb8b211bd39d8b527f3b66207976ef9f2f106230/setuptools-1.4.2.tar.gz

tar -xf setuptools-1.4.2.tar.gz

cd setuptools-1.4.2

sudo python setup.py install

##### install pip for python 2.4.3

wget https://pypi.python.org/packages/25/57/0d42cf5307d79913a082c5c4397d46f3793bc35e1138a694136d6e31be99/pip-1.1.tar.gz

tar -xf pip-1.1.tar.gz

cd pip-1.1

sudo python setup.py install
