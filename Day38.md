# Day 38-50 Days of Code

 Date: 08-07-2026

---

##  DSA Questions Solved
(1D Linked List)
- [Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)
- [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

### C++ Code 

[Delete Node in a Linked List]
```cpp
    void deleteNode(ListNode* node) {
        
        ListNode* cur = node;
        ListNode* after = node->next;
        
        cur->val=after->val;
        cur->next=after->next;

        delete after;
    }
```

[Middle of the Linked List]
Brute Force:
TC: O(n+n/2) ~ O(n)
SC: O(1)
```cpp
 ListNode* middleNode(ListNode* head) {

        if(head==nullptr || head->next==nullptr) return head;
        int len=0;
        ListNode* temp=head;

        while(temp!=nullptr){
            len++;
            temp=temp->next;
        }

        int mid=(len/2)+1;
        temp=head;

        int cnt=1;
        while(cnt<mid){
            temp=temp->next;
            cnt++;
        }
        return temp;
    }
```

Optimal: 
TC: O(n/2)
SC: O(1)

```cpp
 ListNode* middleNode(ListNode* head) {

        if(head==nullptr || head->next==nullptr) return head;
    
        ListNode* fast=head;
        ListNode* slow=head;
        
        while(fast!=nullptr && fast->next!=nullptr){
            fast=fast->next->next;
            slow=slow->next;
        }

        return slow;

    }
```