最长子数组和

给你一个整数数组 `nums` ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。



**子数组**

是数组中的一个连续部分。



 

**示例 1：**

```
输入：nums = [-2,1,-3,4,-1,2,1,-5,4]
输出：6
解释：连续子数组 [4,-1,2,1] 的和最大，为 6 。
```

**示例 2：**

```
输入：nums = [1]
输出：1
```

**示例 3：**

```
输入：nums = [5,4,-1,7,8]
输出：23
```

 

**提示：**

- `1 <= nums.length <= 105`
- `-104 <= nums[i] <= 104`

两个for循环总是会超时

通过203/210个案例

前缀和

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        vector<int> arr;
        int res = 0;
        arr.push_back(0);
        if((int)nums.size() == 1){
            return nums[0];
        }
        for(int i = 0; i < nums.size(); i ++){
            res = 0;
            int k = 0;
            while(k <= i){
                res += nums[k];
                k ++;
            }
            arr.push_back(res);
        }
        int count = 0;
        int result = -1 * INT_MAX;
        for(int i = 1; i <= arr.size(); i ++){
            count = 0;
            for(int j = i; j < arr.size(); j ++){
                count = arr[j] - arr[i - 1];
                result = count > result ? count : result;
            }
        }
        return result;
    }
};
```

贪心算法：

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int count = 0;
        int res = INT_MIN;
        for(int i = 0; i < (int)nums.size(); i ++){
            count += nums[i];
            if(count > res){
                res = count;
            }
            if(count < 0){
                count = 0;
            }
        }
        return res;
    }
};
```

