```cpp
const int N = 12;
int a[N];     //把整数的每一位数字抠出来，存入数组 
int f[N][10]; //f[i][j]表示一共有i位，且最高位数字为j的Windy数的个数 

void init(){  //预处理Windy数的个数 
  for(int i=0; i<=9; i++) f[1][i]=1;  //一位数 
  for(int i=2; i<N; i++)        //阶段：枚举位数 
    for(int j=0; j<=9; j++)     //状态：枚举第i位 
      for(int k=0; k<=9; k++)   //决策：枚举第i-1位 
        if(abs(k-j)>=2) f[i][j]+=f[i-1][k];    
}
int dp(int x){
  if(!x) return 0;                //特判，x==0返回0 
  int cnt = 0; 
  while(x) a[++cnt]=x%10, x/=10;  //把每一位抠出来存入数组

  int res=0, last=-2;             //last表示上一位数字 
  for(int i=cnt; i>=1; --i){      //从高位到低位枚举 
    int now = a[i];               //now表示当前位数字 
    for(int j=(i==cnt); j<now; ++j)     //最高位从1开始 
      if(abs(j-last)>=2) res+=f[i][j];  //累加答案 
       
    if(abs(now-last)<2) break;  //不满足定义，break 
    last = now;                 //更新last 
    if(i==1) res++;             //特判，走到a1的情况 
  }
  
  for(int i=1; i<cnt; i++)      //答案小于cnt位的 
    for(int j=1; j<=9; j++) 
      res += f[i][j]; 
  return res; 
}
```
