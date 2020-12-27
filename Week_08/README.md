# week8-学习笔记

## 位操作

```cpp
(x & 1) == 1  // 奇数
(x & 1) == 0  // 偶数
x >> 1  // x/2
x & (x-1)  // 清零最低位的1
x & -x  // 得到最低位的1
x & ~x = 0
```

## 排序

### 快速排序

```cpp
int partition(vector<int>& nums, int left, int right) {
    int pivot = nums[left];

    while (left < right) {
        while (left < right && nums[right] >= piovt) {
            right--;
        }
        swap(nums[left], nums[right]);
        while (left < right && nums[left] <= pivot) {
            left++;
        }
        swap(nums[left], nums[right]);
    }

    return left;
}

void quick_sort(vector<int>& nums, int left, int right) {
    if (left < right) {
        int pivot = partition(nums, left, right);
        quick_sort(nums, left, pivot-1);
        quick_sort(nums, pivot+1, right);
    }
}
```

### 堆排序

```cpp
int heapify(vector<int>& nums, int start, int end) {
    int parent = start;
    int child = 2 * parent + 1;

    while (child <= end) {
        if (child + 1 <= end && nums[child] < nums[child+1]) {
            child++;
        }

        if (nums[parent] > nums[child]) {
            return;
        } else {
            swap(nums[parent], nums[child]);
            parent = child;
            child = 2 * parent + 1;
        }
    }
}

void head_sort(vector<int>& nums) {
    int len = nums.size();

    for (int i = len/2-1; i >= 0; --i) {
        heapify(nums, i, len-1);
    }

    for (int i = len-1; i > 0; --i) {
        swap(nums[0], nums[i]);
        heapify(nums, 0, i-1);
    }
}
```

### 归并排序

```cpp
void merge(vector<int> &array, int front, int mid, int end) {
    vector<int> left_array(array.begin() + front, array.begin() + mid + 1);
    vector<int> right_array(array.begin() + mid + 1, array.begin() + end + 1);
    int idx_left = 0, idx_right = 0;
    left_array.insert(left_array.end(), numeric_limits<int>::max());
    right_array.insert(right_array.end(), numeric_limits<int>::max());
    for (int i = front; i <= end; i++) {
        if (left_array[idx_left] < right_array[idx_right]) {
            array[i] = left_array[idx_left];
            idx_left++;
        } else {
            array[i] = right_array[idx_right];
            idx_right++;
        }
    }
}

void merge_sort(vector<int> &array, int front, int end) {
    if (front >= end) {
        return;
    }
    int mid = front + (end - front) / 2;
    merge_sort(array, front, mid);
    merge_sort(array, mid + 1, end);
    merge(array, front, mid, end);
}
```
