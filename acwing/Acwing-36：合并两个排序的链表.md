# Acwing-36：合并两个排序的链表

[原题链接](https://www.acwing.com/problem/content/34/)

## 题目描述

输入两个递增排序的链表，合并这两个链表并使新链表中的结点仍然是按照递增排序的。

**样例**

```
输入：1->3->5 , 2->4->5
输出：1->2->3->4->5->5
```



## 解题思路

二路归并



## 代码

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* merge(ListNode* l1, ListNode* l2) {
        auto head = new ListNode(-1), tail = head;
        while(l1 && l2) {
            if(l1->val < l2->val){
                tail = tail->next = l1;
                l1 = l1->next;
            }else {
                tail = tail->next = l2;
                l2 = l2->next;
            }
        }
        if(l1)  tail->next = l1;
        if(l2)  tail->next = l2;
        return head->next;
    }
};
```

