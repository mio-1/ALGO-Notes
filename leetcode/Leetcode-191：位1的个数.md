# Leetcode-191：位1的个数

[原题链接](https://leetcode.com/problems/number-of-1-bits/)

## 题目描述

编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为汉明重量）。



**示例 1：**

```
输入：00000000000000000000000000001011
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。
```



## 解题思路

**lowbit(x)** 返回 **x** 的二进制表达式中最低位的 **1** 所对应的值。

计算需要减去多少次 **lowbit()** 即可



## 代码

```c++
class Solution {
public:
    uint32_t lowbit(uint32_t x) {
        return x & -x;
    }
    
    int hammingWeight(uint32_t n) {
        int cnt = 0;
        while(n)    n -= lowbit(n), cnt ++;
        return cnt;
    }
};
```

