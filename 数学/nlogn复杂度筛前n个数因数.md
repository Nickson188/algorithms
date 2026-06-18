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
```
