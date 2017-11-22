# Python para cálculo y análisis

Yo importo sin referencia la librería de `numpy` porque me permite usar en modo
silimar a matlab las funciones que uso con mayor regularidad: `array()`,`arange()`, etc


## Código de funciones útiles

smooth
```Python
from numpy import *

def smooth(x, window_len=11, window='hanning'):
    s=r_[2*x[0]-array(x[window_len:1:-1]), x, 2*x[-1]-array(x[-1:-window_len:-1])]
    w = ones(window_len,'d')
    y = convolve(w/w.sum(), s, mode='same')
    return y[window_len-1:-window_len+1]

```

good  Y limit
```Python
from numpy import *
import matplotlib.pyplot as plt

def goodYlim(yy,margin=0.1,offset=0):
    full_range=max(yy)-min(yy)
    gmin=min(yy)-full_range*margin/2 + min(0,offset)*full_range
    gmax=max(yy)+full_range*margin/2 + max(0,offset)*full_range
    return (gmin,gmax)

```
now()
```Python
from datetime import datetime

def now():
    return datetime.now().strftime("%Y%m%d_%H%M%S")

```

Imports típicos:
```Python
from numpy import *
import matplotlib.pyplot as plt

import os
from time import sleep
import time

from datetime import datetime
import subprocess
import glob
import struct
```
