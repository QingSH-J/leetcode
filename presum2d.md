二维前缀和

```c++
#include <iostream>
#include <algorithm>
const int N = 1E5 + 10;

int n, m, q;
int a[N][N], s[N][N];

int main()
{
    std::cin >> n >> m >> q;

    for (int i = 1; i <= n; i ++ )
        for (int j = 1; j <= m; j ++ )
            std::cin >> a[i][j], s[i][j] = s[i][j - 1] + s[i - 1][j] - s[i - 1][j - 1] + a[i][j];

    while (q -- )
    {
        int x1, y1, x2, y2;
        std::cin >> x1 >> y1 >> x2 >> y2;
        std::cout << s[x2][y2] - s[x2][y1 - 1] - s[x1 - 1][y2] + s[x1 - 1][y1 - 1] << endl;
    }
    return 0;
}
```



