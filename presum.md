前缀和，时间复杂度比较高的算法

```c++
#include<iostream>
#include<vector>
int main() {
	std::vector<int> nums;
	int x = 0;
	int n = 0;
	std::cin >> n;
	for (int i = 0; i < n; i++) {
		std::cin >> x;
		nums.push_back(x);
	}
	int res = 0;
	std::vector<int> presum;
	for (int k = 0; k < n; k++) {
		res = 0;
		int dex = k;
		for (int j = 0; j < k; j++) {
			res += nums[j];
		}
		presum.push_back(res);
	}
	int l, r;
	std::cin >> l >> r;
	std::cout << presum[r] - presum[l - 1] << std::endl;
	return 0;
}
```

利用递推公式：

```c++
#include<iostream>
#include<vector>
const int N = 1E5 + 10;
int A[N], pre[N];
int main() {
	int x = 0;
	int n = 0;
	std::cin >> n;
	for (int i = 1; i <= n; i++) {
		std::cin >> x;
		A[i] = x;
	}
	int res = 0;
	for (int i = 1; i <= n; i++) {
		pre[i] = pre[i - 1] + A[i];
	}
	int l, r;
	std::cin >> l >> r;
	std::cout << pre[r] - pre[l - 1] << std::endl;
	return 0;
}
```

