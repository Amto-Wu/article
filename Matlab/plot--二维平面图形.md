plot--二维平面图形

概述：通过描点、连线的方式，绘制二维平面图形

```
plot(X,Y,S)
```

参数说明

> X,Y是向量,分别表示点集的横坐标和纵坐标
>
> S指定绘图时线条的样式

示例

在[0,2*pi]用红线画sin x,用绿圈画cos x. 

```matlab
x=linspace(0,2*pi,30);
y=sin(x);
z=cos(x);
plot(x,y,'r',x,z, 'go')
```

