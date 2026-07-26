```cpp
struct FactorsSieve {
    int N;
    vector<vector<int>> f; 
    FactorsSieve(int n) {
        N = n;
        f.resize(N + 1);
        for (int i = 1; i <= N; i++) {         
            for (int j = i; j <= N; j += i) {   
                f[j].push_back(i);           
            }
        }
    }
    vector<int> get(int x) {
        if (x < 1 || x > N) return {}; 
        return f[x];
    }
};
// 创建筛子，计算 1 到 200 的所有因子
// FactorsSieve fs(200);
// 查询 36 的因子
// vector<int> divs = fs.get(36);
// cout << "36的因子: ";
// for (int d : divs) {
//    cout << d << " ";
// }
```
