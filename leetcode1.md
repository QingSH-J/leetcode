设计一个算法，找出数组中最小的k个数。以任意顺序返回这k个数均可。

**示例：**

```
输入： arr = [1,3,5,7,2,4,6,8], k = 4
输出： [1,2,3,4]
```

**提示：**

- `0 <= len(arr) <= 100000`

- `0 <= k <= min(100000, len(arr))`

  使用优先队列，也就是小根堆来完成

  ```c++
  class Solution {
  public:
      vector<int> smallestK(vector<int>& arr, int k) {
          priority_queue<int, vector<int>, greater<int>> queue;
          int size = int(arr.size());
          for(int i = 0; i < size; i ++){
              queue.push(arr[i]);
          }
          vector<int> newarr;
          for(int i = 0; i < k; i ++){
              int temp = queue.top();
              queue.pop();
              newarr.push_back(temp);
          }
          return newarr;
      }
  };
  ```

  