```cpp
const int N=10010;
vector<int> e[N]; 
int dfn[N],low[N],stk[N],top,scc[N],cnt;
int in[N],out[N]; //SCC的入度,出度

void tarjan(int x){
  dfn[x]=low[x]=++dfn[0]; stk[++top]=x;
  for(int y : e[x]){
    if(!dfn[y]){
      tarjan(y);
      low[x]=min(low[x],low[y]); 
    }
    else if(!scc[y]) low[x]=min(low[x],dfn[y]);
  }
  if(dfn[x]==low[x]){
    ++cnt;
    while(stk[top+1]!=x) scc[stk[top--]]=cnt;
  }
}
```
