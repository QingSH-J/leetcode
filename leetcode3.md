给你两个由正整数和 `0` 组成的数组 `nums1` 和 `nums2` 。

你必须将两个数组中的 **所有** `0` 替换为 **严格** 正整数，并且满足两个数组中所有元素的和 **相等** 。

返回 **最小** 相等和 ，如果无法使两数组相等，则返回 `-1` 。

 

**示例 1：**

```
输入：nums1 = [3,2,0,1,0], nums2 = [6,5,0]
输出：12
解释：可以按下述方式替换数组中的 0 ：
- 用 2 和 4 替换 nums1 中的两个 0 。得到 nums1 = [3,2,2,1,4] 。
- 用 1 替换 nums2 中的一个 0 。得到 nums2 = [6,5,1] 。
两个数组的元素和相等，都等于 12 。可以证明这是可以获得的最小相等和。
```

**示例 2：**

```
输入：nums1 = [2,0,2,0], nums2 = [1,4]
输出：-1
解释：无法使两个数组的和相等。
```

 

**提示：**

- `1 <= nums1.length, nums2.length <= 105`
- `0 <= nums1[i], nums2[i] <= 106`

```c++
class Solution {
public:
    long long minSum(vector<int>& nums1, vector<int>& nums2) {
        int flag1 = 0;
        int flag2 = 0;
        int size1 = (int)nums1.size();
        int size2 = (int)nums2.size();
        long long res1 = 0;
        long long res2 = 0;
        int cnt1 = 0;
        int cnt2 = 0;
        for(int i = 0; i < size1; i++){
            if(nums1[i] == 0){
                flag1 = 1;
                cnt1 ++;
            }
            res1 += nums1[i];
        }
        cout << res1;
        for(int i = 0; i < size2; i++){
            if(nums2[i] == 0){
                flag2 = 1;
                cnt2 ++;
            }
            res2 += nums2[i];
        }
        cout << res2;
        if(flag1 > flag2 && res1 + cnt1 > res2){
            return -1;
        }
        else if(flag2 > flag1 && res2 + cnt2 > res1){
            return -1;
        }
        if(flag1 == 0 && flag2 == 0 && res1 != res2){
            return -1;
        }
        if(res1 + cnt1 >= res2 + cnt2){
            return res1 + cnt1;
        }else{
            return res2 + cnt2;
        }
        if(res2 + cnt2 >= res1 + cnt1){
            return res2 + cnt2;
        }else{
            return res1 + cnt1;
        }
        return 1;
    }
};
```

