```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long
using i128=__int128_t;
using ull = unsigned long long;
#define endl '\n'

int dx[4] = {0, 0, 1, -1};
int dy[4] = {1, -1, 0, 0};

int dxx[8] = {0, 0, 1, -1, -1, 1, -1, 1};
int dyy[8] = {-1, 1, 0, 0, -1, 1, 1, -1};

const int P = 998244353;
const int add = 1000;

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
vector<int> init(int n)
{
    int temp=n;
    set<int> se;
    while(temp>1)
    {
        int p=minp[temp];
        se.insert(p);
        while(minp[temp]==p)
        {
            temp/=p;
        }
    }
    vector<int> p;
    for(auto x:se)
    {
        p.push_back(x);
    }
    return p;
}
int calc(int r,int n)
{
    auto p=init(n);
    // 先计算1-r内与n不互质的个数
    int sz=p.size();
    int res=0;
    for(int i=1;i<(1LL<<sz);i++)
    {
        int cnt=0;
        int v=1;
        for(int j=0;j<sz;j++)
        {
            if((i>>j)&1)
            {
                cnt++;
                v*=p[j];
            }
        }
        if(cnt%2==1)
        {
            res+=r/v;
        }
        else
        {
            res-=r/v;
        }
    }
    return res;
}
signed main()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    sieve(1e7+10);
    int r,n;
    cin>>r>>n;
    int ans=calc(r,n);
    cout<<ans<<endl;
    return 0; 
}
```
