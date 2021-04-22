# Acwing-821：跳台阶

[原题链接](https://www.acwing.com/problem/content/description/823/)

## 题目描述

一个楼梯共有 *n* 级台阶，每次可以走一级或者两级，问从第 *0* 级台阶走到第 *n* 级台阶一共有多少种方案。

**输入格式**

共一行，包含一个整数 *n*。

**输出格式**

共一行，包含一个整数，表示方案数。

**数据范围**

 <font color='maroon'>`1 ≤ n ≤ 15` </font>

**输入样例：**

```
5
```

**输出样例：**

```
8
```



## 解题思路

状态转移方程： <font color='maroon'>`f[n] = f[n - 1] + f[n - 2]` </font>



## 代码

```c++
#include <iostream>

using namespace std;

int main() {
    int n;
    cin >> n;
    // 使用两个数记录，可以减少空间复杂度
    int a = 1, b = 1;
    while( -- n) {
        int c = a + b;
        a = b, b = c;
    }
    cout << b << endl;
    return 0;
}
```

