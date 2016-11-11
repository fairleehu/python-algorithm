# 冒泡排序
##排序的前提，交换值操作
在排序的过程中,会发生两个值进行交换,我们可以通过一个temp值进行交换
```
temp = alist[i]
alist[i] = alist[j]
alist[j] = temp
```
当然在python中，我们可以写出类似这样的表达式a,b=b,a一个语句就解决了  
##冒泡排序的分析
交换过程图示(第一次)：     

![bubblesort](/images/bubblesort.jpg)  

那么我们需要进行n-1次冒泡过程，每次对应的比较次数如下图所示：  

![compare](/images/compare.bmp)
```python
def bubbleSort(alist):
    for passnum in range(len(alist)-1,0,-1):
        for i in range(passnum):
            if alist[i]>alist[i+1]:
                temp = alist[i]
                alist[i] = alist[i+1]
                alist[i+1] = temp

alist = [54,26,93,17,77,31,44,55,20]
bubbleSort(alist)
print(alist)
```
##冒泡排序的演示
效果：   
![bubble](/images/bubble.gif)

##冒泡的缺点
气泡排序通常被认为是最低效的排序方法，因为它必须在最终位置被知道之前交换项目。 这些“浪费”的交换操作是非常昂贵的。 然而，因为气泡排序使得通过列表的整个未排序部分，它有能力做大多数排序算法不能做的事情。 特别地，如果在通过期间没有交换，则我们知道该列表必须被排序。 如果发现列表已排序，可以修改气泡排序以便及早停止。 这意味着对于只需要几个遍的列表，冒泡排序可以具有识别排序列表和停止的优点。
