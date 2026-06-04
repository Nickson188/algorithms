```cpp
const int N=5010;
int n,m,cnt,ans;
vector<pair<int,int>> e[N];
int d[N],vis[N]; //d[i]表示点i到集合内点的最小边权

void prim(){
  for(int i=0;i<=n;i++) d[i]=1e9; d[1]=0;
  for(int i=1,u;i<=n;i++){
    u=0; //0点很大
    for(int j=1;j<=n;j++)if(!vis[j]&&d[j]<d[u]) u=j;
    vis[u]=1;    //选出最优点
    if(u) cnt++; //点数
    ans+=d[u];   //边权和
    for(auto [v,w]:e[u])if(d[v]>w) d[v]=w;
  }
  
  if(cnt==n) printf("%d\n",ans);
  else puts("orz");
}
```
