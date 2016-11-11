# 插入排序
插入排序的基本操作就是将一个数据插入到已经排好序的有序数据中，从而得到一个新的、个数加一的有序数据，算法适用于少量数据的排序，
时间复杂度为O(n^2)，是最稳定的排序方法。

##插入排序分析
![insert](/images/insert.png)
```python
def insertSort(alist):
  for index in range(1,len(alist)):
    currentvalue = alist[index]
    position = index
    while position > 0 and alist[position-1]>currentvalue:
      alist[position]=alist[position-1]
      position = position-1

    alist[position] = currentvalue
alist = [54,26,93,17,77,31,44,55,20]
insertSort(alist)
print(alist)
```

##插入排序演示
![insert](/images/insert.gif)
