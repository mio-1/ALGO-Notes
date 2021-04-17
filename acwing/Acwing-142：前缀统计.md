# Acwing-142：前缀统计

[原题链接](https://www.acwing.com/problem/content/144/)

## 题目描述

给定 *N* 个字符串 ![](https://latex.codecogs.com/svg.image?S_1,S_2...S_N)，接下来进行 *M* 次询问，每次询问给定一个字符串 *T*，求 ![](https://latex.codecogs.com/svg.image?S_1-S_N) 中有多少个字符串是 *T* 的前缀。

输入字符串的总长度不超过 ![](https://latex.codecogs.com/svg.image?10^{6})，仅包含小写字母。

**输入格式**

第一行输入两个整数 *N*，*M*。

接下来 *N* 行每行输入一个字符串 ![](https://latex.codecogs.com/svg.image?S_i)。

接下来 *M* 行每行一个字符串 *T* 用以询问。

**输出格式**

对于每个询问，输出一个整数表示答案。

每个答案占一行。

**输入样例：**

```
3 2
ab
bc
abc
abc
efg
```

**输出样例：**

```
2
0
```



## 解题思路

**核心:**  Trie树的简单应用

存储 -- 与Trie树一致

查询 -- 题目要求统计相同前缀。那么在遍历树的过程中，用一个整数记录所经过节点的cnt值即可



## 代码

```c++
#include <iostream>

using namespace std;

const int N = 1000010;

int n, m;
int son[N][26], cnt[N], idx;

// trie树模板
void insert(string &a) {
    int p = 0;
    for(int i=0; i<a.size(); i++) {
        int u = a[i] - 'a';
        if(!son[p][u]) son[p][u] = ++ idx;
        p = son[p][u];
    }
    cnt[p] ++;
}

int query(string &a) {
    // 用整数res来统计前缀
    int p = 0, res = 0;
    for(int i=0; i<a.size(); i++) {
        int u = a[i] - 'a';
        if(!son[p][u]) return res;
        p = son[p][u];
        res += cnt[p];
    }
    return res;
}

int main() {
    string a;
    cin >> n >> m;
    while(n --) {
        cin >> a;
        insert(a);
    }
    while(m --) {
        cin >> a;
        cout << query(a) << endl;
    }
    return 0;
}
```

