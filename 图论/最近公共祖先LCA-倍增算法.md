```cpp
const int N=500005;
int n,m,s;
vector<int> e[N];
int dep[N],fa[N][21];

void dfs(int x,int f){ //预处理dep,fa数组
  dep[x]=dep[f]+1; fa[x][0]=f;
  for(int i=1;i<=20;i++) fa[x][i]=fa[fa[x][i-1]][i-1];
  for(int y:e[x]) if(y!=f) dfs(y,x);
}
int lca(int x,int y){ //倍增求lca
  if(dep[x]<dep[y]) swap(x,y); //让x更深
  for(int i=20;i>=0;i--)if(dep[fa[x][i]]>=dep[y]) x=fa[x][i]; //x向上跳到y的同一层
  if(x==y) return x;
  for(int i=20;i>=0;i--)if(fa[x][i]!=fa[y][i]) x=fa[x][i],y=fa[y][i]; //x,y一起向上跳
  return fa[x][0];
}
```
