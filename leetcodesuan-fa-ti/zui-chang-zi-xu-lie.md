> 给定一个无序的整数数组，找到其中最长上升子序列的长度。
示例:
输入: [10,9,2,5,3,7,101,18]
输出: 4 
解释: 最长的上升子序列是 [2,3,7,101]，它的长度是 4。

***
1、 因为会出现 2 4 6 3 5 7这种情况，所以使用栈来保存自增序列，如果出现小于的情况，则更新第一个大于的该数的值，这样就能在手续保留出3 5 7的位置出来，很巧。（O(n*logn）
```C
include <iostream>
using namespace std; 
int i,j,n,s,t,a[100001];
int main()
{
cin>>n;
a[0]=-1000000;
for(i=0;i<n;i++)
{
	cin>>t;
	if(t>a[s]) a[++s]=t;
	else
	{
	int l=1,h=s,m;
	while(l<=h)
	{
		m=(l+h)/2;
		if(t>a[m]) l=m+1;
		else h=m-1;
		}
	a[l]=t;
	}
 }
 cout<<s<<endl;
 }

```