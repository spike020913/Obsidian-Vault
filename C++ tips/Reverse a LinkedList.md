```
ListNode* reverseList(ListNode* head) {
        ListNode *prev = nullptr;
        while(head) {
            auto nextNode = head -> next;
            head -> next = prev;                   
            prev = head;                            
            head = nextNode;                        
        }
        return prev;
    }
```