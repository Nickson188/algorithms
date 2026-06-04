```cpp
const int N=200010;
int n,m;
int fa[N],ans,tot;
pair<int,pair<int,int> >e[N]; //边集

int find(int u){ //并查集的找根
  return fa[u]==u?u:fa[u]=find(fa[u]);
}
void kruskal(){
  for(int i=1;i<=n;i++) fa[i]=i;
  sort(e+1,e+1+m); //排序
  for(int i=1;i<=m;i++){
    int x=find(e[i].second.first),y=find(e[i].second.second);
    if(x!=y){
      fa[x]=y;
      ans+=e[i].first;
      if(++tot==n-1) break;
    }
  }
  if(tot==n-1) printf("%d\n",ans);
  else puts("orz");
}
```
