### property属性

1. 在类中，在函数前使用@property装饰器来设置property属性。
2. 使用类属性创建property属性

**函数必须有返回值，且函数不能有参数**

好处：property像使用属性一样，而不再是使用函数，因为我只关心它的值是多少，比使用函数更加的贴近需求。且使用函数时，可能还需要传递参数，property属性没有这种问题。

```python
class Test(object):
    @property
    def test(self): # 不能有参数
        return 100
    
t = Test()
ret = t.test # 像获取属性一样，不能使用函数调用形式
print(ret)
# 100

t.test() # t.test此时它是100这个值，不能作为函数调用
# 'int' object is not callable
```

不能使用函数调用的方式，因为这相当于将该函数成了一个实例属性，它是一个值，它不能调用。



#### 设置property属性以及删除property属性

```python
class Goods(object):
    def __init__(self):
        self.origin_price = 100
        self.discount = 0.8
    
    @property
    def price(self): # 获取属性
        return self.origin_price * self.discount
        
    @price.setter # property属性设置装饰器
    def price(self, value):
        self.origin_price = 200
    
    @price.deleter # property属性删除装饰器
    def price(self):
        del self.origin_price
        
        
g = Goods()
print(g.price) 
g.price = 200 # 自动调用test.setter，
print(g.price)
del g.price # 自动调用test.deleter

'''
80.0
160.0
'''
```



#### 使用类属性创建property属性

```python
class Test(object):
    def get(self): # 获取属性
        print("get")
    
    def set(self, value): # 设置属性
        print("set")
        
    def del_(self): # 删除属性
        print("del")
    
    VALUE = property(get, set, del_) # 创建property属性
    
t = Test()
ret = t.VALUE
t.VALUE = 100
del t.VALUE
'''
get
set
del
'''
```

