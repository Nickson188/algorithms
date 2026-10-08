```cpp
// 返回 (质因子, 对应的幂次) 列表
std::vector<std::pair<int, int>> get_factors_with_count(int x) {
    std::vector<std::pair<int, int>> factors;
    while (x > 1) {
        int p = minp[x];
        int count = 0;
        // 把当前质因子 p 一次性除干净
        while (x % p == 0) {
            count++;
            x /= p;
        }
        factors.push_back({p, count});
    }
    return factors;
}
```
