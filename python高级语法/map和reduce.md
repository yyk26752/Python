###map

`map()`接受两个参数，一个是函数，一个是可迭代对象( `Itearable` )。`map`将传入的函数一次作用到序列的每个元素上，并将结果作为新的迭代器( `Iteraor` )返回。

由于返回的是一个`Iterator`，它是惰性序列(使用时才生成)，所以可以通过`list()`将结果变成`list`。

```python
def f(x):
	return x**2

r = map(f, [1, 2, 3, 4, 5])
print(list(r))
# [1, 4, 9, 16, 25]
```

**把list所有数字转为字符串**

```python
list(map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
# ['1', '2', '3', '4', '5', '6', '7', '8', '9']
```





### reduce

`reduce`把一个函数作用在一个序列上，这个函数**必须接受两个参数**，`reduce`把结果继续和序列的下一个元素进行计算，最终返回计算的结果。

```python
from functools import reduce

def add(x, y):
    return x + y

print(reduce(add, [1, 2, 3, 4, 5])) # 先1+2得3，将3与3继续计算得6，将6与4计算...
# 15
```





####将`str`转化为`int`，不包含负数

```python
from functools import reduce

def f(x, y):
	return x*10 + y

def char2int(s):
    digits = {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}
    return digits[s]

print(reduce(f, map(char2int, "12345")))
# 12345    
```

简化函数

```python
from functools import reduce

DIGITS = {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}

def str2int(s):
    def fn(x, y):
        return x * 10 + y
    def char2num(s):
        return DIGITS[s]
    return reduce(fn, map(char2num, s))
```

