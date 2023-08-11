# Binary Tree

| https://leetcode.com/problems/binary-tree-preorder-traversal/ |
| --- |
| https://leetcode.com/problems/binary-tree-postorder-traversal/ |
| https://leetcode.com/problems/binary-tree-inorder-traversal/ |
| https://leetcode.com/problems/maximum-depth-of-binary-tree/ |
| https://leetcode.com/problems/minimum-depth-of-binary-tree/ |
| https://leetcode.com/problems/diameter-of-binary-tree/ |
| https://leetcode.com/problems/invert-binary-tree/ |
| https://leetcode.com/problems/flatten-binary-tree-to-linked-list/ |
| https://leetcode.com/problems/find-duplicate-subtrees/ |
| https://leetcode.com/problems/count-complete-tree-nodes/ |
| https://leetcode.com/problems/balanced-binary-tree/ |
| https://leetcode.com/problems/binary-tree-paths/ |
| https://leetcode.com/problems/sum-of-left-leaves/ |
| https://leetcode.com/problems/find-bottom-left-tree-value/ |
| https://leetcode.com/problems/path-sum/ |
| https://leetcode.com/problems/path-sum-ii/ |
| https://leetcode.com/problems/flatten-nested-list-iterator/ |
| https://leetcode.com/problems/merge-two-binary-trees/ |
|  |

| Level Order |
| --- |
| https://leetcode.com/problems/binary-tree-level-order-traversal/ |
| https://leetcode.com/problems/binary-tree-level-order-traversal-ii/ |
| https://leetcode.com/problems/binary-tree-right-side-view/ |
| https://leetcode.com/problems/average-of-levels-in-binary-tree/ |
| https://leetcode.com/problems/n-ary-tree-level-order-traversal/ |
| https://leetcode.com/problems/find-largest-value-in-each-tree-row/ |
| https://leetcode.com/problems/populating-next-right-pointers-in-each-node/ |
| https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/ |

| Construction |
| --- |
| https://leetcode.com/problems/maximum-binary-tree/ |
| https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/ |
| https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/ |
| https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/ |
| https://leetcode.com/problems/serialize-and-deserialize-binary-tree/ |

| BST |
| --- |
| https://leetcode.com/problems/kth-smallest-element-in-a-bst/ |
| https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/ |
| https://leetcode.com/problems/convert-bst-to-greater-tree/ |
| https://leetcode.com/problems/validate-binary-search-tree/ |
| https://leetcode.com/problems/search-in-a-binary-search-tree/ |
| https://leetcode.com/problems/insert-into-a-binary-search-tree/ |
| https://leetcode.com/problems/delete-node-in-a-bst/ |
| https://leetcode.com/problems/unique-binary-search-trees-ii/ |
| https://leetcode.com/problems/unique-binary-search-trees/ |
| https://leetcode.com/problems/minimum-absolute-difference-in-bst/ |
| https://leetcode.com/problems/find-mode-in-binary-search-tree/ |
| https://leetcode.com/problems/trim-a-binary-search-tree/ |
| https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/ |
|  |
|  |

| LCA |
| --- |
| https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/ |
| https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iv/ |
| https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/ |
| https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/ |
| https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iii/ |

### 递归遍历模版

```cpp
vector<int> inorderTraversal(TreeNode* root) {
    vector<int> res;
    stack<TreeNode*> stk;
    if (root == nullptr) return res;
    stk.push(root);
    while (!stk.empty()) {
        TreeNode* node = stk.top();
        if (node != nullptr) {
            stk.pop();
            if (node->right) stk.push(node->right); 
            stk.push(node);
            stk.push(nullptr);
            if (node->left) stk.push(node->left);
        } else {
            stk.pop();
            node = stk.top();
            stk.pop();
            res.push_back(node->val);
        }
    }
    return res;
}
```

### 层序遍历模版

```cpp
vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> res;
    queue<TreeNode*> q;
    if (root == nullptr) return res;
    q.push(root);
    while (!q.empty()) {
        vector<int> level;
        int size = q.size();
        for (int i = 0; i < size; ++i) {
            TreeNode* node = q.front();
            q.pop();
            level.push_back(node->val);
            if (node->left) q.push(node->left);
            if (node->right) q.push(node->right);
        }
        res.push_back(level);
    }
    return res;
}
```