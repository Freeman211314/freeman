
***
```
#include <iostream>
 2 using namespace std; 
 3 int i,j,n,s,t,a[100001];
 4 int main()
 5 { 
 6     cin>>n;
 7     a[0]=-1000000;
 8     for(i=0;i<n;i++)
 9     {
10         cin>>t;
11         if(t>a[s]) a[++s]=t;
12         else
13         {
14             int l=1,h=s,m;
15             while(l<=h)
16             {
17                 m=(l+h)/2;
18                 if(t>a[m]) l=m+1;
19                 else h=m-1;
20             }
21             a[l]=t;
22         }
23     }
24     cout<<s<<endl;
25 }
```