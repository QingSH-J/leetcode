## 暴力做法

简称 BF (Brute Force) 算法。该算法的基本思想是从主串 ![S](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 的第一个字符开始和模式串 ![T](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 的第一个字符进行比较，若相等，则继续比较二者的后续字符；否则，模式串 ![T](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 回退到第一个字符，重新和主串 ![S](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 的第二个字符进行比较。如此往复，直到 ![S](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 或 ![T](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) 中所有字符比较完毕。

```c++
#include<iostream>
#include<string>
#include<vector>
//字符串匹配

std::vector<int> BF(std::string a, std::string b, int n, int m) {
	std::vector<int> ans;
	int i, j;
	for (i = 0; i < n - m + 1; i++) {
		for (j = 0; j < m; j++) {
			if (a[i + j] != b[j]) {
				break;
			}
		}
		if (j == m) {
			ans.push_back(i);
		}
	}
	return ans;
}
int main() {
	std::string a = "QingShiyuHAHAQingShiyu";
	std::string bb = "QingShiyu";
	std::vector<int> k = BF(a, bb, a.size(), bb.size());
	for (int num : k) {
		std::cout << num << std::endl;
	}
	return 0;
}
```

