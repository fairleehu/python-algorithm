# 二叉树

##思考：
具有3个结点的二叉树可能有几种不同形态？

##二叉树的基本概念
叉树是每个节点最多有两个子树的树结构。通常子树被称作“左子树”（left subtree）和“右子树”（right subtree）  


##二叉树的性质(特性)
**性质1:** 在二叉树的第i层上至多有2^i-1个结点（i>0）  
**性质2:** 深度为k的二叉树至多有2^k-1个结点（k>0）  
**性质3:** 对于任何一棵二叉树，若2度的结点数有n2个，则叶子数（n0）必定为n2＋1 （即n0=n2+1）   
n2 = 3
n0 = 4
n0 = n2+1   
**性质4:**具有n个结点的完全二叉树的深度必为 log2(n+1)   
**性质5:**对完全二叉树，若从上至下、从左至右编号，则编号为i 的结点，其左孩子编号必为2i，其右孩子编号必为2i＋1；其双亲的编号必为i/2（i＝1 时为根,除外）
  
> (1)完全二叉树——若设二叉树的高度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第h层有叶子结点，并且叶子结点都是从左到右依次排布，这就是完全二叉树。
![完全二叉树](/images/完全二叉树.png)
(2)满二叉树——除了叶结点外每一个结点都有左右子叶且叶子结点都处在最底层的二叉树。
![满二叉树](/images/满二叉树.png)

##二叉树的节点表示以及树的创建
通过使用Node类中定义三个属性，分别为elem本身的值，还有lchild左孩子和rchild右孩子
```python
class Node(object):
    """节点类"""
    def __init__(self, elem=-1, lchild=None, rchild=None):
        self.elem = elem
        self.lchild = lchild
        self.rchild = rchild
```
树的创建,创建一个树的类，并给一个root根节点，一开始为空，随后添加节点
```python
class Tree(object):
    """树类"""
    def __init__(self):
        self.root = Node()

    def add(self, elem):
        """为树添加节点"""
        node = Node(elem)
        if self.root.elem == -1:            #如果树是空的，则对根节点赋值
            self.root = node
        else:
            myQueue = []
            treeNode = self.root
            myQueue.append(treeNode)
            while myQueue:                      #对已有的节点进行层次遍历
                treeNode = myQueue.pop(0)
                if treeNode.lchild == None:
                    treeNode.lchild = node
                    return
                elif treeNode.rchild == None:
                    treeNode.rchild = node
                    return
                else:
                    myQueue.append(treeNode.lchild)
                    myQueue.append(treeNode.rchild)
```