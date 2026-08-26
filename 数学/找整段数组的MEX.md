```cpp
int calc(vector<int> &a)
{
    int n=a.size();
    map<int,int> cnt;
    int v=0;
    for(int i=1;i<=n;i++)
    {
        cnt[a[i]]++;
        while(cnt.count(v))
        {
            v++;
        }
    }
    return v;
}
```
