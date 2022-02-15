priorityqueue

queue：先进先出（first in first out）
stack：先进后出（first in last out）

priorityqueue：保持一定的顺序（order），按顺序出

保持一定的顺序（order）:

1.queue

插入新元素：和原有的每个元素进行比较

时间复杂度：O(MN)

首位出队列：取第一位


2.最大/小堆（heap）

					50
			45					30
		20			10	 	5		 	3
	2		1


插入新元素：在最后插入，自下而上堆化（swim）

首位出队列：自上而下堆化（sink）


ref

https://www.cnblogs.com/DSNFZ/articles/7782292.html




