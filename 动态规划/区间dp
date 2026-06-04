```cpp
// 区间DP O(n^3)
#include<bits/stdc++.h>
using namespace std;

const int N=310;
int n,a[N],s[N];
int f[N][N]; //f[i][j]表示把从i到j合并的最小代价 

int main(){
  cin>>n;
  for(int i=1;i<=n;i++) cin>>a[i],s[i]=s[i-1]+a[i];
  memset(f,0x3f,sizeof(f));
  for(int i=1;i<=n;i++) f[i][i]=0;
  
  for(int len=2; len<=n; len++)     //枚举区间长度
  for(int l=1,r=len; r<=n; l++,r++) //枚举区间端点
  for(int k=l; k<r; k++)            //枚举区间断点
    f[l][r]=min(f[l][r],f[l][k]+f[k+1][r]+s[r]-s[l-1]);
  
  cout<<f[1][n];
}
```
