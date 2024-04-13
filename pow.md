实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 `x` 的整数 `n` 次幂函数（即，`xn` ）。

 

**示例 1：**

```
输入：x = 2.00000, n = 10
输出：1024.00000
```

**示例 2：**

```
输入：x = 2.10000, n = 3
输出：9.26100
```

**示例 3：**

```
输入：x = 2.00000, n = -2
输出：0.25000
解释：2-2 = 1/22 = 1/4 = 0.25
```

 

**提示：**

- `-100.0 < x < 100.0`
- `-231 <= n <= 231-1`
- `n` 是一个整数
- 要么 `x` 不为零，要么 `n > 0` 。
- `-104 <= xn <= 104`

会超时，应对301/307个数据是可以的

```c++
class Solution {
public:
    double myPow(double x, int n) {
        if(n == 0){
            return (double)1;
        }
        if(x == 1){
            return double(1);
        }
        double temp = x;
        if(n > 0){
            while(--n){
                temp *= x;
            }
        }
        if(n < 0){
            x = double(1) / double(x);
            temp = x;
            n = n * -1;
            while(--n){
                temp *= x;
            }
        }
        return temp;
    }
};
```

快速幂（官方）

```c++
class Solution {
public:
    double quickMul(double x, long long N) {
        if (N == 0) {
            return 1.0;
        }
        double y = quickMul(x, N / 2);
        return N % 2 == 0 ? y * y : y * y * x;
    }

    double myPow(double x, int n) {
        long long N = n;
        return N >= 0 ? quickMul(x, N) : 1.0 / quickMul(x, -N);
    }
};

```

