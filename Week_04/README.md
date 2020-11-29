# week4-学习笔记

## DFS代码模板

```c++
// 递归写法
map<int, int> visited;

void dfs(Node* root) {
    if (root == nullptr) return;

    if (visited.count(root->val)) {
        // already visit
        return
    }

    visited[root->val] = 1;

    // process
    for (auto child : root->children) {
        dfs(child);
    }

    return;
}

// 非递归写法
void dfs(Node* root) {
    map<int, int> visited;
    if (root == nullptr) return;

    stack<Node*> stk({root});

    while (!stk.empty()) {
        Node* node = stk.top();
        stk.pop();
        if (visited.count(node->val)) {
            continue
        }
        visited[node->val] = 1;

        for (auto child : node->children) {
            stk.push(child);
        }
    }
    return;
}
```

## BFS代码模板

```c++
void bfs(Node* root) {
    if (root == nullptr) {
        return;
    }

    map<int, int> visited;

    queue<Node*> queue_node({root});

    while (!queue.empty()) {
        Node* node = queue_node.top();
        queue_node.pop;
        if (visited.count(node->val)) {
            continue;
        }
        visited[node->val] = 1;

        for (auto child : node->children) {
            queue_node.push(child);
        }
    }
}
```

## 贪心

好好学动规吧

## 二分查找

强烈推荐python bisect的代码模板

```python
def bisect_left(nums, x):
    """查找插入后保持有序性的最左位置"""
    lo, hi = 0, len(nums)
    while lo < hi:
        mid = (lo+hi) // 2
        if nums[mid] < x:
            lo = mid + 1
        else:
            hi = mid
    return lo

def bisect_right(nums, x):
    """查找插入后保持有序性的最右位置"""
    lo, hi = 0, len(nums)
    while lo < hi:
        mid = (lo+hi) //2
        if nums[mid] <= x:
            lo = mid + 1
        else:
            hi = mid
    return lo
```
