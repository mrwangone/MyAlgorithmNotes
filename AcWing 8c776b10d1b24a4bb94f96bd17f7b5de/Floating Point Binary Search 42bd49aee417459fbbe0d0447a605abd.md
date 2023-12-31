# Floating Point Binary Search

```cpp
bool check(double x) {/* ... */} // 检查x是否满足某种性质

double bsearch_3(double l, double r)
{
    const double eps = 1e-6;   // eps 表示精度，取决于题目对精度的要求
    while (r - l > eps)
    {
        double mid = (l + r) / 2;
        if (check(mid)) r = mid;
        else l = mid;
    }
    return l;
}
```

### E.g Cubic root

```cpp
double l = -10000, r = 10000;
while (r - l > 1e-8) {
	double mid = (l + r) / 2;
	if (mid * mid * mid >= x) r = mid;
	else l = mid;
}
return l;

```