核心思路：利用快慢指针快速找到中点，然后用Merge Sort解决

```
ListNode* sortList(ListNode* head) {
    if (head == nullptr || head->next == NULL)
        return head;
    ListNode *fast = head, *slow = head;
    while(fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    ListNode *r = sortList(slow->next);
    slow->next = NULL;
    ListNode *l = sortList(head);
    return merge(l, r);
}

ListNode *merge(ListNode *l, ListNode *r) {
    ListNode *dummy = new ListNode(0), *node;
    node = dummy;
    while (l && r) {
        if (l->val < r->val) {
            node->next = l;
            l = l->next;
        } else {
            node->next = r;
            r = r->next;
        }
        node = node->next;
    }
    if (l)
        node->next = l;
    else 
        node->next = r;
    return dummy->next;
}
```