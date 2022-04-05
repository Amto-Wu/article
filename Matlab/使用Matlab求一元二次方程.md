使用Matlab求一元二次方程

方法一

```matlab
%% 本程序求解黄金分割率的比值
% r^2 - r - 1 = 0的解就是比值。
p = [1 -1 -1];
% 此数组代表了上式的二次项系数、一次项系数和常数项。
r = roots(p);
print_str = sprintf('r^2 - r - 1 = 0的结果是:%f和%f\n', r);
disp(print_str);
```

方法二

```matlab
r2 = solve('r^2 - r - 1 = 0');
print_str = sprintf('r*r - r - 1 = 0的结果是:%f和%f\n', r2);
disp(print_str);
```

提升结果精度

```
vpa(r,50)			% r为要进行精度提升的数，50表示精确到小数点后的位数
```

