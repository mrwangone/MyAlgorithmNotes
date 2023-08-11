# Reverse linked list

### Reverse Linkedin list

Iteration：

```cpp
ListNode* reverseList(ListNode* head) {
    if (head == nullptr) return nullptr;
    ListNode* prev = nullptr;
    ListNode* cur = head;
    ListNode* next = head->next;
    while (cur) {
        next = cur->next;
        cur->next = prev;
        prev = cur;
        cur = next;
    }
    return prev;
}
```

Recursion:

不要跳进递归，只考虑返回值

```cpp
ListNode* reverseList(ListNode* head) {
    if (head == nullptr || head->next == nullptr) return head;
    ListNode* reverseHead = reverseList(head->next);
    head->next->next = head;
    head->next = nullptr;
    return reverseHead;
}
```

### Swap Nodes in Pairs

Iteration:

```cpp
ListNode* swapPairs(ListNode* head) {
    ListNode* dummyHead = new ListNode(-1, head);
    ListNode* cur = dummyHead;
    while (cur->next && cur->next->next) {
        ListNode* a = cur->next,* b = a->next;
        a->next = b->next;
        cur->next = b;
        b->next = a;
        cur = a;
    }
    return dummyHead->next;   
}
```

Recursion:

```cpp
ListNode* swapPairs(ListNode* head) {
    if (head == nullptr || head->next == nullptr) return head;
    ListNode* a = head, *b = head->next;
    ListNode* tail = swapPairs(b->next);
    b->next = a, a ->next = tail;
    return b;
}
```

### Reverse Between

Iteration:

```cpp
ListNode* reverseBetween(ListNode* head, int left, int right) {
    if (head == nullptr || head->next == nullptr) return head;
    ListNode* dummyHead = new ListNode{-1, head};
    ListNode* before = dummyHead;
    for (int i = 1; i < left; ++i) {
        before = before->next;
    }
    ListNode* nxt;
    ListNode* pre = before->next;
    ListNode* cur = pre->next;
    for (int i = left; i < right; ++i) {
        nxt = cur->next;
        cur->next = pre;
        pre = cur;
        cur = nxt;
    }
    before->next->next = cur;
    before->next = pre;
    return dummyHead->next;
}
```

Recursion:

```cpp
ListNode* successor;

ListNode* reverseBetween(ListNode* head, int left, int right) {
    if (left == 1) {
        return reverseN(head, right);
    }
    head->next = reverseBetween(head->next, left - 1, right - 1);
    return head;
}

ListNode* reverseN(ListNode* head, int n) {
    if (n == 1) {
        successor = head->next;
        return head;
    }
    ListNode* last = reverseN(head->next, n - 1);
    head->next->next = head;
    head->next = successor;
    return last;
}
```

### Reverse in k pairs

Iteration:

![Untitled](Reverse%20linked%20list%20836b1dee05d64173a0a7db040799c6d8/Untitled.png)

```cpp
ListNode* reverseKGroup(ListNode* head, int k) {
    auto dummyHead = new ListNode(-1, head);
    auto p = dummyHead;
    while (true) {
        auto q = p;
        for (int i = 0; i < k && q; ++i) q = q->next;
        if (!q) break;
        auto a = p->next, b = a->next;
        for (int i = 0; i < k - 1; ++i) {
            auto c = b->next;
            b->next = a;
            a = b, b = c;
        }
        auto c = p->next;
        p->next = a;
        c->next = b;
        p = c;
    }
    return dummyHead->next;
}
```

Recursion:

```cpp
ListNode* reverseKGroup(ListNode* head, int k) {
    if (head == nullptr) return nullptr;
    // 区间 [a, b) 包含 k 个待反转元素
    ListNode *a, *b;
    a = b = head;
    for (int i = 0; i < k; i++) {
        // 不足 k 个，不需要反转，base case
        if (b == nullptr) return head;
        b = b->next;
    }
    // 反转前 k 个元素
    ListNode *newHead = reverse(a, b);
    // 递归反转后续链表并连接起来
    a->next = reverseKGroup(b, k);

    return newHead;
}
```