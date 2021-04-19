# Acwing-68：0到n-1中缺失的数字

[原题链接](https://www.acwing.com/problem/content/64/)

## 题目描述

一个长度为 *n−1* 的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围 *0* 到 *n−1* 之内。

在范围 *0* 到 *n−1* 的 *n* 个数字中有且只有一个数字不在该数组中，请找出这个数字。

**样例**

```
输入：[0,1,2,4]
输出：3
```



## 解题思路

使用高斯求和公式

![](https://latex.codecogs.com/svg.image?\sum_{i=1}^{n}i&space;=&space;\left&space;(1&space;&plus;&space;n&space;&space;\right&space;)&space;*&space;n&space;/&space;2)

可以求出 *1 ~ n* 的所有数之和，然后减去所给数组中所有数的和，**差值就是缺失的数**



## 代码

```c++
class Solution {
public:
    int getMissingNumber(vector<int>& nums) {
        int sum = 0, n = nums.size();
        for(auto i : nums)  sum += i;
        return (1 + n) * n / 2 - sum;
    }
};
```

