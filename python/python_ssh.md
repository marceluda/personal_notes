# Python SSH

Sobre cómo hacer para ejecutar cosas de forma remota en python y SSH


## En linux


## En windows

Voy a guardar momentaneamente este draft, que no es muy bueno. Hay que reescribirlo
usando popen o algo así

Primero hay que usar `pagent` para definir el host y la conexión sin password

Luego, esto funca pero te abre una consola `cmd` en cada ejecución.


```python
import os
from time import sleep
import numpy as np
import matplotlib.pyplot as plt
tamfig=(19, 9.5)
folder='C:\\Users\\Pato\\Desktop\\RP'
os.chdir(folder)
plink='plink.exe  -load "rp-XXXXXX.local" -l root -batch /root/RP_py/'
dec=64 # Data decimation, supports only this values: 1,8, 64,1024,8192,65536
trig=4
dt=8e-9*dec
num_med=3
# Con este comando haces que el trigguer coincida con t=0
os.system(plink+'osc_set.py TrgDelay 16383')
plt.figure(figsize=tamfig)
pp=np.ndarray(num_med,dtype=object)
for i in range(num_med):
#    os.system('plink.exe  -load "rp-XXXXXX.local" -l root -batch /root/RP_py/osc_trig.py dec=8 trig=6 > pp.txt')
    os.system(plink+'osc_trig.py dec={:d} trig={:d} > pp.txt'.format(dec,trig))
    pp[i]=np.genfromtxt ('pp.txt', delimiter=",")
    plt.subplot(211); plt.plot(pp[i][:,0]*dt,pp[i][:,1]/2**13)
    plt.subplot(212); plt.plot(pp[i][:,0]*dt,pp[i][:,2]/2**13)
```
