Matlab使用一

## 注释

> %这是注释

## 变量命名

> 变量名可由`字母、数字、下划线`构成，当变量名只能由`字母`开头

## 快捷键

> CTRL+Q				关闭Matlab
>
> Ctrl+R　：注释（对多行有效）
>
> Ctrl+T　：取消注释（对多行注释有效）　
>
> Ctrl+Z　：取消上一次操作　　
>
> Ctrl+I   ：自动缩进（对多行有效）
>
> Ctrl+[   ：减少缩进（对多行有效）
>
> Ctrl+]   ：增加缩进（对多行有效）　　
>
> ↑光标键 ：选择最近的一次命令（命令模式下）　
>
> Esc：清除当前行（命令模式下）

## 快捷命令

- 删除变量

  ```matlab
  clear				%删除所有变量
  clear 变量名		  %删除指定变量
  ```

- 清屏

  ```matlab
  clc					%只是清屏，不会删除变量
  ```

- 查看已经创建的的变量

  ```matlab
  who					%列出已经创建的变量
  whos				%详细列出已经创建的变量，包括字节长、类型等
  ```

- 查看关键字

  ```matlab
  iskeyword
  ```

- 快速查看文件内容

  ```
  type 文件名
  ```

- 查看文件寻找路径

  ```
  path
  ```

- 保存工作空间中的所有变量，文件以`.mat`结尾

  ```
  save
  或
  save 保存的文件名
  ```

- 将 `.mat` 文件中保存的变量拷贝到工作空间中

  ```
  load 文件名
  ```

  

## 基本操作

1.强制类型转换

```matlab
baseNum = 123.456;
toUint8 = uint8(baseNum);
toUint32 = uint32(baseNum);
whos;
```

2.在图形上加格栅、图例和标注

```matlab
GRID ON		% 加格栅在当前图上
GRID OFF	% 删除格栅

xlabel(string)		% 在当前图形的x轴上加图例string
ylabel(string)		% 在当前图形的y轴上加图例string
zlabel(string)		% 在当前图形的z轴上加图例string
title(string)		% 在当前图形的顶端上加图例string
```

```matlab
x=linspace(0,2*pi,30);
y=sin(x);
plot(x,y)
xlabel('自变量X')
ylabel('函数Y')
title('示意图')
grid on
```

3.自定义标注位置

```matlab
gtext('string')			% 绘图后使用鼠标自定义标注位置
```

```matlab
x=linspace(0,2*pi,30);
y=sin(x);
z=cos(x);
plot(x,y,x,z)
gtext('sin(x)');gtext('cos(x)')
```

4.指定义坐标系范围

```matlab
axis([xmin xmax ymin ymax zmin zmax])
```

```matlab
x=linspace(0.0001,0.01,1000);
y=sin(1./x);
plot(x,y)
axis([0.005 0.01 –1 1])
```

5.图形保持

```matlab
% 保持当前图形, 以便继续画图到当前图上
hold on
% 释放当前图形窗口
hold off
```



## 后记

关于语句结尾是否加 `;`

当加 `;` 时，执行该语句后，会将该语句的结果在控制台中输出。不加 `;` 时，执行该语句后，不会将该语句的结果在控制台中输出。

```matlab
% 这里是注释行,这个文件演示如何使用文件编辑代码
disp('首先演示后面都加了分号的代码');
age = 20;
name = 'chuckiezhu';
sentence = '你好啊!';
print_str = sprintf('%s年龄是%d.他说:"%s"\n', name, age, sentence);
% sprintf是格式化字符串的函数，返回一个格式化后的字符串
disp(print_str);  % 显示目标字符串
disp('---------------分割线---------------------')
disp('然后演示后面都不加分号的代码')
age = 20
name = 'chuckiezhu'
sentence = '你好啊!'
print_str = sprintf('%s年龄是%d.他说:"%s"\n', name, age, sentence)
% sprintf是格式化字符串的函数，返回一个格式化后的字符串
disp(print_str)  % 显示目标字符串
```

