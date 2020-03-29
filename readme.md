
#  DFS (backtracking 枚举法)

>它是什么类型的问题，一般解决那种input类型的题）
>recursion，解决需要infinit for loop 才能解决的问题.
ex. subset
	for（int） {
		for (int ...)
			......
		}
	input: [1,2,3]
	output: [1], [1,2] [1,2,3] [1,3] [2] [2,3] [3]


## Template

```java
void dfs (int start, int end, int[]input ,List<T>path, List<List<T>> result) {
	if(start >= end) {
		//result.add(path); //case 1
		return;
	}
	//terminate: think start as a pointer, as long as start pointing pointing to the end pointer
	
	//Second for loop
	for ( int i = start /*case 1*/; i <= end; i++) { //case 2: i = 0
		path.add(input[i]);
		dfs(i+1, end, input, path, result);
		path.remove(path.size() - 1); //backtracking: [1,2,3] remove 3 and 2, 
										//increment start pointer (at the second loop) from 2 to 3, then it's [1,3]
	}
}
```

## samples/examples
permutation
permutation2
subset1
subset2
combination
combination2
Letter Combinations of a phone number
n-queens

## Discussion/Resource/Reading Material
[https://leetcode.com/problems/subsets/discuss/27281/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partitioning)](https://leetcode.com/problems/subsets/discuss/27281/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partitioning))


## Time Complexity

Subset O(2^n)
combination: O(k * C(n, k))
>reference: [https://www.1point3acres.com/bbs/thread-117602-1-1.html](https://www.1point3acres.com/bbs/thread-117602-1-1.html)

## Space Complexity

> recursion (stack) + data structure
> Interesting fact: output: true/false, memo, input : 5998

## 题目分析 (as long as it's a classical question)

> question description
> link
> sample test cases
> 总结： brute-force， optimized
> 解法 ：1. describe algorithm 2. graph explanation
> code : brute-force sol,  optimized sol (find out points that can be optimized: duplicate, extra memory etc. cracking coding interview p67)
> analysis : time/space complexity for each solution
> test cases: how to test your program
