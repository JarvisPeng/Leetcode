[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)  
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.  
Example:Input: 1->2->4, 1->3->4  Output: 1->1->2->3->4->4  
# solution
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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode result = ListNode(0);//记录初始节点
        struct ListNode  *result_c = &result;
        while ((l1!=NULL) && (l2!= NULL)){
            if (l1->val < l2->val){
                result_c->next = l1;
                l1 = l1->next;
            }else{
                result_c->next = l2;
                l2 = l2->next;
            }
            result_c = result_c->next;
        }
        result_c->next = (l1==NULL?l2:l1);
        return result.next;
        
    }
};
```
