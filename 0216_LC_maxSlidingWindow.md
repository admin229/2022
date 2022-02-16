滑动窗口最大值



队列：

底层数据结构可以是顺序存储线性表或者链表，后者的操作的时间复杂度为O(1)。


链表：




循环队列：

是对顺序线性表的优化，但容量一定。

front指向头节点，rear指向下一个要插入值的节点

删除：(front + 1) % size, rear stay
新增：front stay, (rear + 1) % size

size = (rear - front + size) % size
isempty = front == rear
isfull = (rear + 1) % size = front 







