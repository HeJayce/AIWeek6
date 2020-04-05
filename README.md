# 人工智能
## 梯度下降法
是一个一阶最优化算法，通常也称为最陡下降法，但是不该与近似积分的最陡下降法混淆。 要使用梯度下降法找到一个函数的局部极小值，必须向函数上当前点对应梯度（或者是近似梯度）的反方向的规定步长距离点进行迭代搜索。如果相反地向梯度正方向迭代进行搜索，则会接近函数的局部极大值点；这个过程则被称为梯度上升法。
## 具体算法
已知一个方程，首先分别求出它每个变量的偏导数，给定一个变量的初始值，分别带入偏导数中，求出梯度。接着将每个变量的梯度与设置好的步长相乘，得出该变量的位移偏量。用变量的初始值加上变量的位移片偏量，得出下一组变量值，以此类推。直到趋于稳定，得出结果。
### 导入函数库
```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl
import math
from mpl_toolkits.mplot3d import Axes3D
import warnings
```
### 设置函数
```python
#原函数
def f2(x, y):
    value = x**2+2*y**2-4*x-2*x*y
    return  value
## 偏函数
def hx1(x, y):
    value = 2*x-4-2*y
    return  value
def hx2(x, y):
    value = 4*y-2*x
    return value
```
### 设置初始值和变化量
```python
x1 = 1
x2 = 1
alpha = 0.05
```
### 循环求出位移偏量与原变量的差值
```python
while(y_change > 1e-10 and iter_num < 100) :
#设置100为迭代次数
    tmp_x1 = x1 - alpha * hx1(x1,x2)
    tmp_x2 = x2 - alpha * hx2(x1,x2)
    tmp_y = f2(tmp_x1,tmp_x2)
    
    f_change = np.absolute(tmp_y - f2(x1,x2))
    x1 = tmp_x1
    x2 = tmp_x2
    GD_X1.append(x1)
    GD_X2.append(x2)
    GD_Y.append(tmp_y)
    iter_num += 1
```
### 输出结果
```python 
print(u"最终结果为:(%.5f, %.5f, %.5f)" % (x1, x2, f2(x1,x2)))
print(u"迭代过程中X的取值，迭代次数:%d" % iter_num)
print(GD_X1) 
```
### 作图
```python
fig = plt.figure(facecolor='w',figsize=(20,18))
ax = Axes3D(fig)
ax.plot(GD_X1,GD_X2,GD_Y,'ko-')
ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_zlabel('z')
plt.show()
```
![image](https://github.com/HeJayce/AI/blob/master/%E8%BF%90%E8%A1%8C%E7%BB%93%E6%9E%9C.png)


### 运行结果
![image](https://github.com/HeJayce/AI/blob/master/%E8%BF%90%E8%A1%8C%E7%BB%93%E6%9E%9C.png)

