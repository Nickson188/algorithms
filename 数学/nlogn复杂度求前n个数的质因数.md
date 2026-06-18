```cpp
std::vector<int> minp, primes;
void sieve(int n) {
    minp.assign(n + 1, 0);primes.clear();
 
    for (int i = 2; i <= n; i++) {
        if (minp[i] == 0) {
            minp[i] = i;
            primes.push_back(i);
        }
 
        for (auto p : primes) {
            if (i * p > n) break;
            minp[i * p] = p;
 
            if (p == minp[i]) break;
        }
    }
}
vector<vector<int>> fac(1e6+1);
void init(){
    sieve(1e6+10);
    for(int i = 1;i<=1e6;i++){
        int t = i;
        while(t != 1){
            int p = minp[t];
            while(minp[t] == p) t /= p;
            fac[i].push_back(p);
        }
    }
}
```
