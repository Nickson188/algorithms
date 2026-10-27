```cpp
const int N = 2e5 + 10;
int f[N][32];
// f[i][j] 表示从起点 i 开始、长度为 2^j 的区间内的最大值
int n;
void build() {
	int m = log2(n) + 1;
	for (int j = 0; j < m; j ++)
		for (int i = 1; i <= n - (1ll << j) + 1; i ++)
			if (!j) f[i][j] = sum[i];
			else f[i][j] = max(f[i][j - 1], f[i + (1ll << (j - 1))][j - 1]);
}
// 查询区间最大值
int query(int l, int r) {
	int len = r - l + 1, k = log2(len);
	return max(f[l][k], f[r - (1ll << k) + 1][k]);
}
```
