ezplot--符号函数(显函数、隐函数和参数方程)画图

使用

```matlab
% 表示在a<x<b绘制显函数f=f(x)的函数图
ezplot('f(x)',[a,b])
```

```matlab
% 表示在区间xmin<x<xmax和 ymin<y<ymax绘制隐函数f(x,y)=0的函数图
ezplot('f(x,y)',[xmin,xmax,ymin,ymax])
```

```matlab
% 表示在区间tmin<t<tmax绘制参数方程x=x(t),y=y(t)的函数图
ezplot('x(t)','y(t)',[tmin,tmax])
```

示例
$$
在[0,pi]上画 y=cos x 的图形
$$

```matlab
ezplot('sin(x)',[0,pi])
```

$$
在[0,2*pi]上画出 x=cos^3t,y=sin^3t
$$

```
ezplot('cos(t)^3','sin(t)^3',[0,2*pi])
```


$$
在[-2,0.5],[0,2]上画出隐函数e^x+sin(xy)=0的图
$$


```
ezplot('exp(x)+sin(x*y)',[-2,0.5,0,2])
```

















