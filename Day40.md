# Day 40-50 Days of Code

 Date: 11-07-2026

---

##  DSA Questions Solved
(1D Linked List)
- [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
- [Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

### C++ Code 

Remove Nth Node From End of List
Brute:
```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        int len=0;
        ListNode* temp=head;
        if(head==nullptr) return head;

        while(temp){
            temp=temp->next;
            len++;
        }

        if(n>len) return nullptr;
        int idx=len-n+1;

        temp=head;
        ListNode* prev=nullptr;
        int cnt=1;
        
        if(idx==1){
            temp=head;
            head=head->next;
            delete temp;
            return head;
        }

        while(temp!=nullptr && cnt!=idx){
            prev=temp;
            temp=temp->next;
            cnt++;
        }

        prev->next=temp->next;
        delete temp;
        return head;

    }
```

Optimal:

```cpp
 ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        ListNode* fast = head;

        for(int i=0;i<n;i++){
            fast=fast->next;
        }
        if(fast==nullptr) {
            ListNode* temp=head->next;
            delete head;
            return temp;
        }

        ListNode* slow=head;
        while(fast->next!=nullptr){
            fast=fast->next;
            slow=slow->next;
        }

        ListNode* temp=slow->next;
        slow->next=slow->next->next;
        delete temp;
        return head;

    }
```


Delete the Middle Node of a Linked List
```cpp
  ListNode* deleteMiddle(ListNode* head) {
        
        ListNode* slow=head;
        ListNode* fast=head;
        ListNode* prev;

        if(head==nullptr || head->next==nullptr) return nullptr;  

        while(fast!=nullptr && fast->next!=nullptr){
            prev=slow;
            slow=slow->next;
            fast=fast->next->next;
        }
        prev->next = slow->next;
        delete slow;

        return head;
        
    }
```