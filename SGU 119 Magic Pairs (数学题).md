---
title: SGU 119 Magic Pairs (数学题)
tags:
  - SGU
  - 数学
date: 2014-03-11 23:00:17
---

   <span style="font-family:arial,helvetica,sans-serif;">网上找到一个写的不错的证明：</span>

	<span style="font-family:arial,helvetica,sans-serif;">   <span style="color: rgb(85, 85, 85); line-height: 24px;">要证明一个东西：若</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![forall x,y in mathbb{N}, N mid A_0 x+B_0 y](http://d.ream.at/wp-content/plugins/latex/cache/tex_e173725a3011148dbad09a46b9856098.gif)</span><span style="color: rgb(85, 85, 85); line-height: 24px;">，则</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![A equiv A_0 i ~(mod N), ~B equiv B_0 i ~(mod N), ~(0 le i < N)](http://d.ream.at/wp-content/plugins/latex/cache/tex_cdeaff7a7f93931a49f8e1fb065dc125.gif)</span><span style="color: rgb(85, 85, 85); line-height: 24px;">是</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![N mid Ax+By](http://d.ream.at/wp-content/plugins/latex/cache/tex_f15166f7a07df025cfc99295d86ae9e3.gif)</span><span style="color: rgb(85, 85, 85); line-height: 24px;">的充要条件。</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">　　证明：</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">1)充分性：显然。</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">2)必要性：</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">若</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![N mid A_0 x+B_0 y](http://d.ream.at/wp-content/plugins/latex/cache/tex_96c5e542a343ab36992eeff5e6af2257.gif)</span><span style="color: rgb(85, 85, 85); line-height: 24px;">，则 </span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![N mid Ax+By](http://d.ream.at/wp-content/plugins/latex/cache/tex_f15166f7a07df025cfc99295d86ae9e3.gif)</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">=> 若</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![A_0 x+B_0 y equiv 0 ~(mod N)](http://d.ream.at/wp-content/plugins/latex/cache/tex_6f12d22025d41929910969c083d49b44.gif)</span><span style="color: rgb(85, 85, 85); line-height: 24px;">，则</span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![(A-A_0 i)x+(B-B_0 i)y equiv 0 ~(mod N)](http://d.ream.at/wp-content/plugins/latex/cache/tex_20bf8aafeb9b3ce4b325db417cf1988a.gif)</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">=> </span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![left{begin{array}{l}A equiv A_0 cdot (i+1) ~(mod N)\ B equiv B_0 cdot (i+1) ~(mod N)end{array}right.](http://d.ream.at/wp-content/plugins/latex/cache/tex_498c0af838203ce818ac6d7cd92fce43.gif)</span>

	<span style="color: rgb(85, 85, 85); line-height: 24px;">即 </span><span class="MathJax_Preview" style="margin: 0px; padding: 0px; color: rgb(85, 85, 85); line-height: 24px;">![left{begin{array}{l}A equiv A_0 cdot i ~(mod N)\ B equiv B_0 cdot i ~(mod N)end{array}right.](http://d.ream.at/wp-content/plugins/latex/cache/tex_724e5b85870230c885d6e2d051b91aa1.gif)</span></span>

	   上面的网址：[http://d.ream.at/sgu-119/](http://d.ream.at/sgu-119/)

	    自己想的时候并没有那么复杂

	    ax + by = kn，那么acx + by = kcn的，如果c > n 的话，就可以提取出一个anx + bny = knn出来约去，所以所有的可能就是枚举c 为 0到n - 1，每次(ac % n, bc % c)就是一组。

	    其实这样子还是有重复的，这个式子首先得除掉gcd(a,b,n)然后得出来的r作为c枚举的范围，不然范围比较大？反正减小范围，因为枚举0到n-1会有重复的ab组。

	    还有那个上面的移位再比较实在有点赞～少写点代码

	 

<pre class="brush:cpp">
/* From: Lich_Amnesia
 * Time: 2014-03-11 22:39:02
 *
 * SGU 119
 * */
#include <iostream>
#include <cstdio>
#include <algorithm>
#include <cstring>
#include <cmath>
#include <queue>
#include <set>
#include <vector>
using namespace std;

const int INF = ~0u>>1;
typedef pair <int,int> P;
#define MID(x,y) ((x+y)>>1)
#define iabs(x) ((x)>0?(x):-(x))
#define REP(i,a,b) for(int i=(a);i<(b);i++)
#define FOR(i,a,b) for(int i=(a);i<=(b);i++)
#define pb push_back
#define mp make_pair
#define print() cout<<"--------"<<endl
int ans[10100];
int gcd(int a,int b){
	return b == 0 ? a : gcd(b, a % b);
}

int main(){
	int n;
	int a,b;
	scanf("%d%d%d", &n, &a, &b);
	int r = n / gcd(gcd(a,b),n);
	for (int i = 0; i < r; i ++){
		ans[i] = (a * i % n << 16) + b * i % n;
	}
	sort(ans,ans + r);
	printf("%dn", r);
	for (int i = 0; i < r; i ++){
		printf("%d %dn",ans[i] >> 16, ans[i] & 0xffff);
	}
	return 0;
}
</pre>

	 