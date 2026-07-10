```cpp
// floor(sqrt(x))
int calc(int x)
{
    int y=sqrt(x);
    while(y*y>x)
    {
        y--;
    }
    while((y+1)*(y+1)<=x) 
    {
        y++;
    }
    return y;
}
```
