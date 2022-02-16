# 数组中的第K个最大元素
给定整数数组 nums 和整数 k，请返回数组中第 k 个最大的元素。

<br>

## 1 题解

解法1: 最大元素可以通过遍历一次，更新截至目前最大元素来求解，将这个方法一般化：存一个目前最大的k的元素的列表，每次跟这个列表的最小值进行比较。（priorityqueue）

解法2: sort一遍。（quicksort/mergesort）

解法3: quicksort的中间解。

<br>

## 2 sort 算法

### 2.1 quicksort

本身是一种分治算法。

shuffle -> partition -> sort

时间复杂度：O(nlgn) (sort一次需要n，平均需要sort lgn次)

    vector<int> sort(vector<int> v) {
        vector<int> left;
        vector<int> right;
        int mid = v[v.size()/2];
        for (auto i : v) {
            if (i < mid) left.emplace_back(i);
            else right.emplace_back(i);
        }
        return sort(left).append(sort(right));
    }

由于只需要找到kth largest

    int kthlargest(vector<int> v, k) {
        vector<int> left;
        vector<int> right;
        if (right.size() >=k )
        int mid = v[v.size()/2];
        for (auto i : v) {
            if (i < mid) left.emplace_back(i);
            else right.emplace_back(i);
        }
        if (right.size() > k) {
            return kthlargest(right);
        } else if (right.size() < k) {
            return kthlargest(left, k-right.size());
        } else return mid;
        
    }

<br>

### 2.2 mergesort

divide -> sort -> merge

时间复杂度：O(nlgn)

<br>

## 3 priorityqueue

queue：先进先出（first in first out）
stack：先进后出（first in last out）

priorityqueue：保持一定的顺序（order），按顺序出

<br>

**3.1 queue**

插入新元素：和原有的每个元素进行比较

首位出队列：取第一位

时间复杂度：O(N$^2$) & 1

<br>

**3.2 二叉堆（heap）& 堆排序（heapsort）**

					50
			45					30
		20			10	 	5		 	3
	2		1


插入新元素：在最后插入，自下而上堆化（swim）

首位出队列：自上而下堆化（sink）

时间复杂度：O(nlgn) & O(nlgn)

**树结构本身不存在，仅以列表序号换算元素在二叉树的位置**

<br>

# ref

https://leetcode-cn.com/problems/kth-largest-element-in-an-array/

https://www.cnblogs.com/DSNFZ/articles/7782292.html






