JSON

## 简介

该模块是 JSON 内置模块，用于处理 JSON 数据

主要使用四个函数

|             |                                          |
| ----------- | ---------------------------------------- |
| json.dumps  | 将 Python 对象编码成 JSON 字符串         |
| json.loads  | 将已编码的 JSON 字符串解码为 Python 对象 |
| json.dump() | 将 JSON 数据写入文件                     |
| json.load() | 读取文件中的 JSON 数据                   |

## 非持久化JSON操作

封装 JSON 数据

```python
#json.dumps()	将 Python 对象编码成 JSON 字符串，结果是json格式的字符串

import json
dict_data = {'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5}

# 编码为 JSON 格式数据
json_data1 = json.dumps(dict_data)

# 编码为 JSON 格式数据，并进行格式化
json_data2 = json.dumps(dict_data, sort_keys=True, indent=4, separators=(',', ': '))

print(json_data1)
print('-'*20)
print(json_data2)
```

解析 JSON 数据

```python
#json.loads()	将已编码的 JSON 字符串解码为 Python 对象

import json

jsonData = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

text = json.loads(jsonData)
print(text)
```

## 持久化 JSON 操作

将 JSON 数据写入文件

```python
# 写入 JSON 数据
with open('data.json', 'w') as f:
    json.dump(data, f)
```

从文件中读取 JSON 数据

```python
# 读取数据
with open('data.json', 'r') as f:
    data = json.load(f)
```

## 后记

python 原始类型向 json 类型的转化对照表：

| Python           | JSON   |
| :--------------- | :----- |
| dict             | object |
| list, tuple      | array  |
| str, unicode     | string |
| int, long, float | number |
| True             | true   |
| False            | false  |
| None             | null   |

json 类型转换到 python 的类型对照表：

| JSON          | Python    |
| :------------ | :-------- |
| object        | dict      |
| array         | list      |
| string        | unicode   |
| number (int)  | int, long |
| number (real) | float     |
| true          | True      |
| false         | False     |
| null          | None      |