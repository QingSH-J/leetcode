![image-20240411161626373](C:\Users\YMY520\AppData\Roaming\Typora\typora-user-images\image-20240411161626373.png)

注意到每次都选择礼物数量最多的堆，那么可以考虑使用大根堆来解决此题

代码如下

`#include<iostream>
#include<queue>
#include<math.h>
using namespace std;
typedef long long ll;
class Solution {
public:
    int res = 0;
    long long pickGifts(vector<int>& gifts, int k) {
        priority_queue<int, vector<int>, less<int>> heap;
        for (int i = 0; i < int(gifts.size()); i++) {
            heap.push(gifts[i]);
        }
        for (int i = 0; i < k; i++) {
            int temp = heap.top();
            if (temp == 1) {
                continue;
            }
            heap.pop();
            temp = (int)sqrt(temp);
            heap.push(temp);
        }
        while(!heap.empty()) {
            int temp = heap.top();
            cout << temp << endl;
            res += temp;
            heap.pop();
        }
        return (ll)res;
    }
};
int main() {
    vector<int> gifts = {1, 1, 1, 1};
    Solution solve;
    auto ans = solve.pickGifts(gifts, 4);
    cout << ans << endl;
    return 0;
}`