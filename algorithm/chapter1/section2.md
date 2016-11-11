# 算法效率衡量
##python一些内置类型操作性能分析
**list的操作测试**

```
def test1():
   l = []
   for i in range(1000):
      l = l + [i]
def test2():
   l = []
   for i in range(1000):
      l.append(i)
def test3():
   l = [i for i in range(1000)]
def test4():
   l = list(range(1000))

from timeit import Timer

t1 = Timer("test1()", "from __main__ import test1")
print("concat ",t1.timeit(number=1000), "milliseconds")
t2 = Timer("test2()", "from __main__ import test2")
print("append ",t2.timeit(number=1000), "milliseconds")
t3 = Timer("test3()", "from __main__ import test3")
print("comprehension ",t3.timeit(number=1000), "milliseconds")
t4 = Timer("test4()", "from __main__ import test4")
print("list range ",t4.timeit(number=1000), "milliseconds")

# ('concat ', 1.7890608310699463, 'milliseconds')
# ('append ', 0.13796091079711914, 'milliseconds')
# ('comprehension ', 0.05671119689941406, 'milliseconds')
# ('list range ', 0.014147043228149414, 'milliseconds')
```


**list的pop操作效率测试**
```
x = list(range(2000000))
pop_zero = Timer("x.pop(0)","from __main__ import x")
print("pop_zero ",pop_zero.timeit(number=1000), "milliseconds")
x = list(range(2000000))
pop_end = Timer("x.pop()","from __main__ import x")
print("pop_end ",pop_end.timeit(number=1000), "milliseconds")

# ('pop_zero ', 1.9101738929748535, 'milliseconds')
# ('pop_end ', 0.00023603439331054688, 'milliseconds')
```
测试pop操作：从结果可以看出，pop最后一个元素的效率远远高于pop第一个元素
> 可以自行尝试下list的append(value)和insert(0,value),即一个后面插入和一个前面插入？？？


那么只通过简单的时间是能判断算法的效率，但是并不是很方便，所以需要一种算法效率的度量方法！
##大O表示法
**规则**  
（1）判断一个算法的效率时，往往只需要关注操作数量的最高次项，其它次要项和常数项可以忽略
（2）在没有特殊说明时，我们所分析的算法的时间复杂度都是指最坏时间复杂度  
（3）只有常数项记做1  
（4）操作数量的估算可以作为时间复杂度的估算  

**常见的时间复杂度**  


|执行次数函数	|阶	|非正式术语|
|-----------|:--------:|:-------|
|12	|O(1)|	常数阶|
|2n+3	|O(n)	|线性阶|
|3n2+2n+1|	O(n2)|	平方阶|
|5log2n+20	|O(logn)	|对数阶|
|2n+3nlog2n+19	|O(nlogn)	|nlogn阶|
|6n3+2n2+3n+4	|O(n3)	|立方阶|
|2n	|O(2n)	|指数阶|

常见的时间复杂度之间的关系  
![算法效率关系](/images/算法效率关系.bmp)

所消耗的时间从小到大
```
O(1) < O(logn) < O(n) < O(nlogn) < O(n2) < O(n3) < O(2n) < O(n!) < O(nn)
```

> 练习：
时间复杂度练习( 参考算法的效率规则判断 )  
O(5)  
O(2n + 1)  
O(n²+ n + 1)  
O(3n³+1)  

##list固定操作的算法复杂度
![list操作](/images/list操作.png)

##dict固定操作的算法复杂度
![dict操作](/images/dict操作.png)
