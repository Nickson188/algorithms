```cpp
const int N=10010,M=500010,inf=(1<<31)-1;
int n,m,s,a,b,c;
int h[N],to[M],w[M],ne[M],tot;
void add(int a,int b,int c){
  to[++tot]=b;w[tot]=c;ne[tot]=h[a];h[a]=tot;
}
int d[N],vis[N];

void spfa(){
  for(int i=1;i<=n;i++) d[i]=inf; d[s]=0;
  queue<int>q; q.push(s); vis[s]=1; //标记在队中
  while(q.size()){
    int u=q.front(); q.pop(); vis[u]=0; //标记不在队中
    for(int i=h[u];i;i=ne[i]){
      int v=to[i];
      if(d[v]>d[u]+w[i]){ //松弛
        d[v]=d[u]+w[i];
        if(!vis[v]) q.push(v),vis[v]=1; //不在队中才入队
      }
    }
  }
}
```
