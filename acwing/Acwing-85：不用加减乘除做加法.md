# Acwing-85：不用加减乘除做加法

[原题链接](https://www.acwing.com/problem/content/81/)

## 题目描述

写一个函数，求两个整数之和，要求在函数体内不得使用 ＋、－、×、÷ 四则运算符号。

#### 样例

```
输入：num1 = 1 , num2 = 2
输出：3
```



## 解题思路

不进位加法： <font color='maroon'>`sum = num1 ^ num2` </font>

进位： <font color='maroon'>`carry = (num1 & num2) << 1` </font>

 <font color='maroon'>`num1 + num2 == sum + carry` </font>

 <font color='maroon'>`carry ` </font>不断左移，最终会变为 <font color='maroon'>`0` </font>，此时  <font color='maroon'>`num1 + num2 == sum` </font>



## 代码

```c++
class Solution {
public:
    int add(int num1, int num2){
        while(num2) {
            int sum = num1 ^ num2;
            int carry = (num1 & num2) << 1;
            num1 = sum, num2 = carry;
        }
        return num1;
    }
};
```

