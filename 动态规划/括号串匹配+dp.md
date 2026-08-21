```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long
using i128=__int128_t;
using ull = unsigned long long;
using ld = long double;
#define endl '\n'

int dx[4] = {0, 0, 1, -1};
int dy[4] = {1, -1, 0, 0};

int dxx[8] = {0, 0, 1, -1, -1, 1, -1, 1};
int dyy[8] = {-1, 1, 0, 0, -1, 1, 1, -1};

const int P = 1e9+7;
const int add = 10000000;

signed main()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int T = 1;
    // cin >> T;
    while(T--)
    {
        int n;
        cin>>n;
        string s;
        cin>>s;
        s=" "+s;
        vector<int> a(n+1);
        for(int i=1;i<=n;i++)
        {
            cin>>a[i];
        }
        vector<int> stk;
        vector<int> match(n+1,0);
        for(int i=1;i<=n;i++)
        {
            if(s[i]=='a')
            {
                stk.push_back(i);
            }
            else
            {
                if(stk.size())
                {
                    match[i]=stk.back();
                    stk.pop_back();
                }
            }
        }
        vector<int> dp(n+1,-1e18);
        dp[0]=0;
        for(int i=1;i<=n;i++)
        {
            if(match[i])
            {
                dp[i]=max(dp[i],dp[match[i]-1]);
                // 如果i位置有匹配,可以将match[i]到i位置删除
            }
            dp[i]=max(dp[i],dp[i-1]+a[i]);
        }
        cout<<dp[n]<<endl;
    }      
    return 0; 
}   
```
