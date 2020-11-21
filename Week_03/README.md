# week2-学习笔记

## 递归

key: 找到最近最简方法，将其拆解成重复子问题


代码模板

```c++
void recur(int level, int param) {
    // 递归终止条件
    if (level >  MAX_LEVEL) {
        return;
    }

    // 处理当前逻辑
    process(level, param);

    // drill down
    recur(level+1, new_param);
}
```

## 分治

代码模板

```python
def divide_conquer(problem, params):
    if problem is None:
        print_result()
        return

    data = prepare_data(problem)
    sub_problem = split_problem(problem, data)

    # conquer sub_problem
    sub_res[0] = divide_conquer(sub_problem[0], params)
    sub_res[1] = divide_conquer(sub_problem[1], params)
    sub_res[2] = divide_conquer(sub_problem[2], params)
    # ...

    # process and generate final result
    result = process_result(sub_res)
```

## 回溯

解体框架

1. 画出决策树

2. dfs

```python
result = []

def bucktracking(path, 选择列表):
    if 满足条件:
        result.append(path)
        return

    for 选择 in 选择列表:
        做选择
        backtracking(path, 选择列表)
        撤销选择
```
