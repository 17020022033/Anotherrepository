# 160. 相交链表
## 题目
编写一个程序，找到两个单链表相交的起始节点。  

例如，下面的两个链表：  
```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
```
在节点 c1 开始相交。  
 
注意：  

如果两个链表没有交点，返回 null.  
在返回结果后，两个链表仍须保持原有的结构。  
可假定整个链表结构中没有循环。  
程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。  
## 思路
假设有两个指针，一个先遍历一次A链表再遍历一次B链表，另一个先遍历一次B链表再遍历一次A链表。  
这样的话，如果它们有可以重合的地方的话，就肯定可以相遇的√  
如果没有，就在他们遍历完，下一个元素都同时是NULL的时候返回NULL。  
进行遍历之前先查一查是不是空的链表。  
## 代码实现
```ruby
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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *Aa=headA;
        ListNode *Bb=headB;
        if(Aa==NULL||Bb==NULL)
            return NULL;
        if(Aa==Bb)
            return Aa;
        while(Aa!=NULL&&Bb!=NULL)
        {
            if(Aa==Bb)
                return Aa;
            if(Aa->next==NULL&&Bb->next==NULL)
                return NULL;
            Aa=Aa->next;
            Bb=Bb->next;
            if(Aa==NULL) 
                Aa=headB;
            if(Bb==NULL)
                Bb=headA;
        }
    }
};
```
