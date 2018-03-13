# TEXT

##### Python 2.4+, 3.x portable excepton handling
```
import sys
try:
    ...
except Exception:
    t, e = sys.exc_info()[:2]
    print(e)
```

##### String to Datetime

from datetime import datetime
```
datetime_object = datetime.strptime('date time string', 'datetime format')
```
e.g. to convert 2001/11/01 14:12:00 to a datetime object
```
datetime_object = datetime.strptime('2001/11/01 14:12:00', '%Y/%m/%d %H:%M:%S')
```
Formats (2): https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior

Formats (3): https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior

##### Datetime to Epoch

(datetime.datetime(2012,04,01,0,0) - datetime.datetime(1970,1,1)).total_seconds()

##### CSV Writing



##### stdin json formatter

cat file.json | python -m json.tool 

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
