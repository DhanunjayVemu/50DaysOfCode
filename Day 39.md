# Day 39-50 Days of Code

 Date: 09-07-2026

---

##  DSA Questions Solved
(1D Linked List)
- [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

### C++ Code 


[Reverse Linked List]
Brute force: 
TC: O(n)
SC: o(n)

```cpp
ListNode* reverseList(ListNode* head) {
        
        vector<int> arr;

        ListNode* temp=head;
        while(temp){
            arr.push_back(temp->val);
            temp=temp->next;
        }
        int n = arr.size();
        temp=head;
        for(int i=n-1;i>=0;i--){
            temp->val=arr[i];
            temp=temp->next;
        }
        return head;
    }
```

optimal (iterative):
TN: O(n)
SC: O(1)
```cpp
ListNode* reverseList(ListNode* head) {
        
       ListNode* temp=head;
       ListNode* front;
       ListNode* prev=nullptr;

       while(temp!=nullptr){
            front=temp->next;
            temp->next=prev;
            prev=temp;
            temp=front;
       }
       return prev;
    }   
```
Recursive: 
TC: O(N)
SC: O(N) - because of recursive stack space for the recursion steps

```cpp
    ListNode* reverseList(ListNode* head) {

        if(head==nullptr || head->next==nullptr){
            return head;
        }  
        ListNode* newhead=reverseList(head->next);
        ListNode* temp=head->next;
        temp->next=head;
        head->next=nullptr;
        return newhead;       
    }  
```

[Linked List Cycle]
TC: ~O(n)
SC: O(1)
```cpp
bool hasCycle(ListNode *head) {
        
        ListNode* slow=head;
        ListNode* fast=head;

        while(fast!=nullptr && fast->next!=nullptr){
            slow=slow->next;
            fast=fast->next->next;
            if(slow==fast) return true;
        }        
        return false;
    }
```

[Linked list cycle II]

```cpp

ListNode* detectCycle(ListNode* head) {

        ListNode* slow = head;
        ListNode* fast = head;
        int flag = 0;
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) {
                slow = head;

                while (slow != fast) {
                    slow = slow->next;
                    fast = fast->next;
                }
                return fast;
            }
        }
            return nullptr;
    }
```