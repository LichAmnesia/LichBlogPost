---
title: SGU 112 a^b-b^a (高精度)
tags:
  - SGU
  - 高精度
date: 2014-01-01 16:36:47
---

主类名必须为Solution，SGU的FAQ里面有写

<pre class="brush:java">
import java.io.*;
import java.math.BigInteger;
import java.util.*;
public class Solution{
	public static void main(String[] args){
		Scanner in = new Scanner(System.in);
		int a = in.nextInt();
		int b = in.nextInt();
		BigInteger A = BigInteger.valueOf(a);	
		A = A.pow(b);
		BigInteger B = BigInteger.valueOf(b);
		B = B.pow(a);
		System.out.println(A.subtract(B));
	}
}
</pre>

	 