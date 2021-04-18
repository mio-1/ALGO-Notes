# Leetcode-456：132模式

[原题链接](https://leetcode.com/problems/132-pattern/)

## 题目描述

给你一个整数数组 <font color='maroon'>`nums` </font> ，数组中共有  <font color='maroon'>`n` </font> 个整数。

**132 模式的子序列** 由三个整数  <font color='maroon'>`nums[i]` </font>、<font color='maroon'>`nums[j]`</font> 和 <font color='maroon'>`nums[k]`</font> 组成，并同时满足：<font color='maroon'>`i < j < k`</font> 和 <font color='maroon'>`nums[i] < nums[k] < nums[j]`</font>

如果  <font color='maroon'>`nums ` </font>中存在 **132 模式的子序列** ，返回  <font color='maroon'>`true` </font> ；否则，返回  <font color='maroon'>`false ` </font>。



## 解题思路

从后往前遍历，利用**单调栈**，并使用  <font color='maroon'>`right` </font> 记录 满足要求 （ <font color='maroon'>`i < j && nums[i] > nums[j]` </font>）的**最大**的 <font color='maroon'>`nums[j]` </font>

若遍历过程中有 <font color='maroon'>`nums[i] < right` </font>，则必存在132模式



## 代码

```c++
class Solution {
public:
    bool find132pattern(vector<int>& nums) {
        int right = INT_MIN;
        stack<int> stk;
        for(int i = nums.size() - 1; i >= 0; i --) {
            if(nums[i] < right) return true;
            // 单调栈寻找满足要求的jk对中最大的nums[k]
            while(stk.size() && stk.top() < nums[i]){
                right = max(right, stk.top());
                stk.pop();
            }
            stk.push(nums[i]);
        }
        return false;
    }
};
```

