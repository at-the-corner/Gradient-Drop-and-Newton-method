#--coding:utf-8--
import numpy as np

def f(x):
    return x*np.sin(x)
#一阶导数
def df(x):
    return np.sin(x)+x*np.cos(x)
#牛顿法
def Newton(f,x_left,x_right):
    ans=[]#极值数组
    x_step=x_left#循环变量
    dx=1e-6
    iter=4000#迭代次数
    #取x范围内所有整数点为起始点进行计算
    while x_left<=x_step<=x_right:
        x=x_step
        for i in range(iter):
            derivative=(df(x+dx)-df(x))/dx
            x_tmp=x-df(x)/derivative#牛顿法
            if x_tmp>=x_right or x_tmp<=x_left:
                break
            x=x_tmp
        ans.append([f(x),x])#向极值数组写入数据
        x_step+=1
    return min(ans)#取最小极值和对应的极值点
res=Newton(f,-6,8)
print 'When x=',res[1],',the minimum of y=xsinx is',res[0]
