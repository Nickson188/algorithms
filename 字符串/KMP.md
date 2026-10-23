```cpp
std::vector<int> kmp(std::string &s)
{
    int n = s.size();
    std::vector<int> next(n + 1);
    for (int i = 1, j = 0; i < n; i++)
    {
        while (j && s[i] != s[j]) j = next[j];
        if (s[i] == s[j]) j++;
        next[i + 1] = j;
    }
    return next;
}
// next[i]表示字符串s的前i个字符组成的子串(s[0....i-1])中,最长的既是前缀又是后缀的真子串(不包含子串本身)的长度
```
