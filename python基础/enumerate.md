### enumerate

该函数可将一个可遍历的数据对象（如list，元组等）组合为一个**索引序列**，同时列出数据和数据下标。

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']

for i, name in enumerate(seasons):
	print(i, name)
    
# out:
0 Spring
1 Summer
2 Fall
3 Winter
```

enumerate第二个参数可以**指定下标的起始位置**。

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']

for i, name in enumerate(seasons, 3):
	print(i, name)
    
# out:
3 Spring
4 Summer
5 Fall
6 Winter
```

