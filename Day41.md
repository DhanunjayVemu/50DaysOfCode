# Day 41-50 Days of Code

 Date: 15-07-2026

---

##  DSA Questions Solved
(1D Linked List)
- [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
- [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

### C++ Code 

[Palindrome Linked List]
TC: O(2N)
```cpp
ListNode* reverseLL(ListNode* head){
        ListNode* prev=nullptr;
        ListNode* cur=head;
        ListNode* temp;

        if(head==nullptr || head->next==nullptr) return head;

        while(cur!=nullptr){
            temp=cur->next;
            cur->next=prev;
            prev=cur;
            cur=temp;
        }
    return prev;
    }
    
    bool isPalindrome(ListNode* head) {
        
        ListNode* slow=head;
        ListNode* fast=head;

        while(fast!=nullptr && fast->next!=nullptr){
            slow=slow->next;
            fast=fast->next->next;
        }

        ListNode* newhead=reverseLL(slow);
        
        ListNode* temp=head;
        while(newhead!=nullptr){
            if(temp->val!=newhead->val) return false;
            newhead=newhead->next;
            temp=temp->next;
        }
        return true;

    }
```


[Add Two Numbers]
```cpp
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        
        int summ=0;
        int carry=0;
        ListNode* result=new ListNode();
        ListNode* temp=result;
        
        while(l1!=nullptr || l2!=nullptr || carry){
            summ=0;
            if(l1!=nullptr){
                summ+=l1->val;
                l1=l1->next;
            }

            if(l2!=nullptr){
                summ+=l2->val;
                l2=l2->next;
            }

            summ+=carry;
            carry=summ/10;
            ListNode* node=new ListNode(summ%10);

            temp->next=node;
            temp=temp->next;
        }
        return result->next;

    }
```