zip

zip 方法是python内置方法，在 Python 2 和 Python 3 中的不同：在 Python 3.x 中为了减少内存，zip() 返回的是一个对象（惰性求值）。如需展示列表，需手动 list() 转换（其他方法也可）

```python
a = [1,2,3]
b = [4,5,6]
c = [4,5,6,7,8]
d=zip(a,b)
for i in d:
    print(i)
print(d)
print(type(d))
# 以下这句会报错
# print(d[0])
```

总结

- 参数经 `zip` 函数处理后，元素个数与最短的列表一致
- 经 `zip` 处理后返回的对象，是惰性求值