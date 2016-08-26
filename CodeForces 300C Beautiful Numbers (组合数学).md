---
title: CodeForces 300C Beautiful Numbers (组合数学)
tags:
  - CodeForces
  - 数学
date: 2014-01-21 14:44:35
---

### 
	[300C - Beautiful Numbers](http://codeforces.com/contest/300/problem/C "Codeforces Round 181 (Div. 2)")

	Let&#39;s <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_MOD_&thinsp;=&thinsp;1000000007</span>. Let&#39;s precalc factorial values modulo <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_MOD_</span>. <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_fact_[_i_]&thinsp;=&thinsp;_i_!%_MOD_</span>, ![](http://espresso.codeforces.com/f691c5d2e09040e3b2eb0fd91ef55156145242f3.png). Let <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_i_</span> be an amount of digits equal to <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_a_</span> in current excellent number. In this case we can find sum of digits in this number: <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_sum_&thinsp;=&thinsp;_ai_&thinsp;+&thinsp;_b_(_n_&thinsp;-&thinsp;_i_)</span>. If <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_sum_</span> is good, then add <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_C_[_n_][_i_]</span> to answer. In this problem it&#39;s impossible to calculate binomial coefficients using Pascal&#39;s triangle, because of large <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_n_</span>. However it can be done this way <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_C_[_n_][_i_]&thinsp;=&thinsp;_fact_[_n_]_inv_(_fact_[_n_&thinsp;-&thinsp;_i_]_fact_[_i_])</span>. <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_inv_(_a_)</span> is multiplicative inverse element(modulo <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_MOD_</span>).<span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_MOD_</span> is a prime number, so <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_inv_(_a_)&thinsp;=&thinsp;_a_<span class="upper-index" style="font-size: 13px; line-height: 0; position: relative; vertical-align: baseline; top: -0.5em;">_MOD_&thinsp;-&thinsp;2</span></span>. Calculating this values for each <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_i_</span> from <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">0</span> to <span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_n_</span> will give correct answer in<span class="tex-span" style="font-size: 18px; font-family: 'times new roman', sans-serif;">_O_(_nlog_(_MOD_))</span>.

	[http://codeforces.com/blog/entry/7497](http://codeforces.com/blog/entry/7497)

	借用一下,组合数学的乘法逆元的求法,先记一下，以后可能会用到

	 

<pre class="brush:cpp">
/* From: Lich_Amnesia
 * Time: 2014-01-21 14:32:49
 *
 * CF 300C Round181_div2 
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
typedef long long ll;
const ll MOD = 1000000007;

bool check(int a, int b,int x){
	while (x){
		if (x % 10 != a && x % 10 != b) return false;
		x /= 10;
	}
	return true;
}

ll Pow_mod(ll a,ll n){
	ll ret = 1;
	while (n){
		if (n & 1) ret = ret * a % MOD;
		a = a * a % MOD;
		n >>= 1;
	}
	return ret;
}

int main(){
	int a,b,n;
	cin >> a >> b >> n;	
	int sum = 0;
	ll ret = 1;
	ll ans = 0;
	for (int i = 0; i <= n; i ++){
		sum = a * i + b * (n - i);
		if (check(a,b,sum)){
			ans = (ans + ret) % MOD;
		}
		ret = ret * (n - i) % MOD;
		ret = ret * Pow_mod(i + 1, MOD - 2) % MOD; 
	} 
	cout << ans << endl;
	return 0;
}
</pre>

	 