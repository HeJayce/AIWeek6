import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl
import math
from mpl_toolkits.mplot3d import Axes3D
import warnings
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
 
x1 = 1
x2 = 1
alpha = 0.05
#保存梯度下降经过的点
GD_X1 = [x1]
GD_X2 = [x2]
GD_Y = [f2(x1,x2)]
# 定义y的变化量和迭代次数
y_change = 1
iter_num = 0
 
while(y_change > 1e-10 and iter_num < 100) :
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
print(u"最终结果为:(%.5f, %.5f, %.5f)" % (x1, x2, f2(x1,x2)))
print(u"迭代过程中X的取值，迭代次数:%d" % iter_num)
print(GD_X1) 
