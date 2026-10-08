```cpp
// 当数值d达到1e12级别时,无法开辟大小为1e12的数组
// 预处理1e6(sqrt(1e12))的质数+试除法
// 任意合数d必定存在一个不超过根号d的质因子
//欧拉筛
std::vector<int> minp, primes;
// minp[i] i的最小质因子
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
vector<int> get(int d)
{
    vector<int> fac;
    for(auto p:primes)
    {
        if(p*p>d)
        {
            break;
        }
        if(d%p==0)
        {
            fac.push_back(p);
            while(d%p==0)
            {
                d/=p;
            }
        }
    }
    if(d>1)
    {
        fac.push_back(d);
    }
    return fac;
}
```
