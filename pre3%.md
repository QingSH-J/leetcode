![image-20240412184338184](C:\Users\YMY520\AppData\Roaming\Typora\typora-user-images\image-20240412184338184.png)

是否为3的倍数，只需要每位加起来可以被3整除即可

代码：

```c++
#include<iostream>
#include<vector>
const int N = 1E5 + 10;
int A[N], pre[N];
int main() {
	int x = 0;
	int n = 0;
	int q = 0;
	std::cin >> n >> q;
	for (int i = 1; i <= n; i++) {
		std::cin >> x;
		A[i] = x;
	}
	int res = 0;
	for (int i = 1; i <= n; i++) {
		pre[i] = pre[i - 1] + A[i];
	}
	int l, r;
	while (q) {
		std::cin >> l >> r;
		if ((pre[r] - pre[l - 1]) % 3 == 0) {
			printf("YES");
		}
		else {
			printf("NO");
		}
	}
	return 0;
}
```

