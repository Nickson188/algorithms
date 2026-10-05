```cpp
template<class T>
class TreePre{
private:
    int n,idx = 0,root;
    vector<vector<pair<int,int>>> &g;
    vector<int> val;
    void dfs1(int u,int f){
        fa[u] = f;
        siz[u] = 1;
        for(auto [v,w]:g[u]){
            if(v!=f){
                dep[v] = dep[u]+1;
                dis[v] = dis[u]+w;
                dfs1(v,u);
                siz[u] += siz[v];
                if(siz[son[u]]<siz[v]) son[u] = v;
            }
        }
    }
    void dfs2(int u,int tp){
        if(u == tp) pre[u] = val[u];
        else pre[u] = pre[fa[u]]^val[u];
        dfn[u] = ++idx;
        idfn[idx] = u;
        top[u] = tp;
        if(son[u]) dfs2(son[u],tp);
        for(auto [v,w]:g[u]){
            if(v!=fa[u] and v != son[u]){
                dfs2(v,v);
            }
        }
    }
public:
    TreePre(vector<vector<pair<int,int>>> &g,vector<int> &val,int root):
        g(g),n(g.size()-1),root(root),dep(n+1),top(n+1),son(n+1),fa(n+1),
        siz(n+1),dfn(n+1),idfn(n+1),dis(n+1),pre(n+1),val(val)
        {
            dep[root] = 1;
            dis[root] = 0;
            dfs1(root,0);
            dfs2(root,root);
        }

    vector<int> dfn,idfn,siz,fa,dep,top,son;
    vector<T> dis,pre;
    pair<T,int> getLca(int u,int v){
        int res = 0;
        while(top[u] != top[v]){
            if(dep[top[u]] > dep[top[v]]){
                u = fa[top[u]];
                res ^= pre[u];
            }else{
                v = fa[top[v]];
                res ^= pre[v];
            }
        }
        if(dep[u]>dep[v]) swap(u,v);
        
        if(u == top[u]) res ^= pre[v];
        else res ^= pre[v]^pre[fa[u]];

        return {u, res};
        // lca=u
    }
    T getDis(int u,int v,int lca){
        return dis[u]+dis[v]-2*dis[lca];
    }
};
// TreePre<int> pre(e,c,1);
// e为边数组 c为大小为n+1的空数组 1是根节点
```
