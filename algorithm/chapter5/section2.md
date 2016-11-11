# 选择排序
选择排序改进了气泡排序，每次通过列表只做一次交换。 为了做到这一点，一个选择排序寻找最大的值，因为它通过，并在完成通过后，将其放置在正确的位置。 与气泡排序一样，在第一次通过后，最大的项目在正确的地方。

##选择排序分析
排序过程：
![selectionsort](/images/selectionsort.jpg)  

```python
def selectionSort(alist):
  for index in range(len(alist)-1,0,-1):
    positionMax = 0
    for location in range(1,index+1):
      if alist[location]>alist[positionMax]:
        positionMax = location
    temp = alist[index]
    alist[index] = alist[positionMax]
    alist[positionMax] = temp

alist = [54,226,93,17,77,31,44,55,20]
selectionSort(alist)
print(alist)
```

##选择排序演示
![selection](/images/selection.gif)
