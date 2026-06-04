```cpp
const int N=100010;
vector<pii> e[N];
int n,m,s;
int d[N],vis[N];

void dijkstra(){
  memset(d,0x3f,sizeof d); d[s]=0;
  priority_queue<pii,vector<pii>,greater<pii> > q; //小根堆
  q.push({0,s});
  while(q.size()){
    auto u=q.top().second; q.pop();
    if(vis[u])continue; vis[u]=1; //不是第1次出队就跳过，是就标记
    for(auto [v,w]:e[u]){
      if(d[v]>d[u]+w){
        d[v]=d[u]+w;
        q.push({d[v],v});
      }
    }
  }
}
```
