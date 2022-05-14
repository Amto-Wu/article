fplot(‘fun’,lims)

表示绘制字符串fun指定的函数在lims=[xmin,xmax]的图形.


注意：
1. fun必须是M文件的函数名或是独立变量为x的字符串.  
2. fplot函数不能画参数方程和隐函数图形，但在一个图上可以画多个图形.

示例

```matlab
% 在[-2,2]范围内绘制函数tanh的图形.
fplot('tanh',[-2,2])
```

```matlab
% 一次性绘制多个函数
fplot('[tanh(x),sin(x),cos(x)]',2*pi*[-1 1 -1 1])
```

