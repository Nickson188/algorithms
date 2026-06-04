```cpp
const int N=110;
int n,m,a,b,c;
int d[N][N];

void floyd(){
  for(int k=1; k<=n; k++)
    for(int i=1; i<=n; i++)
      for(int j=1; j<=n; j++)
        d[i][j]=min(d[i][j],d[i][k]+d[k][j]);
}
```
