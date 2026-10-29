```cpp
template<class T>
struct SparseTable {
    int n;
    std::vector<T> a;
    std::vector<std::array<T, 30>> f;
    std::function<T(T, T)> func;

    SparseTable() {};

    SparseTable(std::vector<T> init_, std::function<T(T, T)> func_) {
        work(init_, func_);
    }

    void work(std::vector<T> &init_) {
        work(init_, [&](T x, T y) { return std::max(x, y); });
    }

    void work(std::vector<T> &init_, std::function<T(T, T)> func_) {
        this->a = init_;
        this->func = func_;
        this->n = a.size();
        this->f.assign(n, {});
        for (int i = 0; i < n; i++) f[i][0] = a[i];
        for (int j = 1; j <= std::__lg(n) + 1; j++) {
            for (int i = 0; i + (1 << j) - 1 < n; i++) {
                f[i][j] = func(f[i][j - 1], f[i + (1 << (j - 1))][j - 1]);
            }
        }
    }

    T query(int l, int r) {
        int k = std::__lg(r - l + 1);
        return func(f[l][k], f[r - (1 << k) + 1][k]);
    }
};
// vector<int> a={3,1,4,1,5,9,2,6};
// SparseTable<int> st_max;
// st_max.woek(a);
// st_max.query(l,r);
// 通过 lambda 表达式自定义求区间最小值 (Min)
// SparseTable<int> st_min;
// st_min.work(a,[](int x,int y)){
//     return min(x,y);
// };
// st_min.query(l,r);
```
