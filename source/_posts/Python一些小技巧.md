---
title: Python一些小技巧
date: 2016-10-10 15:31:11
categories: "Python"
tags:
- 学习
---


## 列表 ##
### 排序 ###
1. 列表和字典的混合排序
<!-- more -->
```python
persons = [{'name':'zhang3','age':15},{'name':'li4','age':12}]
persons.sort(lambda a,b:a['age']-b['age']) # 按照年龄排序
```

### 两个列表的差异 ###
1. 交集
```python
a = [1,2,3]
b = [2,3,4]
value = [v for v in a if v in b]
```

2. 差集
```python
...
value = [v for v in a if not v in b]
```

## 日期 ##
### datetime ###
1. 获得今天时间凌晨，格式：'2016-11-02 00:00:00'
```python
now = datetime.datetime.today().replace(hour=0,minute=0,second=0,microsecond=0)
```
2. 时间相加减
```python 
d1 = datetime.datetime.now()
d2 = d1 + datetime.timedelta()
```
其中`timedelta`方法可以以下几个日期参数进行修改
> days=0,seconds=0,microseconds=0,milliseconds=0,minutes=0,hours=0,weeks=0
