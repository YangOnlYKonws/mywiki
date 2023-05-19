## 前言

动态规划相关，dp的题目都在这

## DP基本五步

1. dp数组以及下标的含义
2. 递推公式
3. dp数组如何初始化
4. 遍历循序
5. 打印数组

可以遵循这五部来写题，网上很多教程不多说

## 题目：

### 斐波那契

#### 基础题：

##### 1.[爬楼梯](https://leetcode.cn/problems/climbing-stairs/)

基础题目，用来熟练动态规划，不多说，斐波那契数列，但是可以拓展，题目只是说一步能迈一个台阶或者两个台阶，如果是M步呢，这可以拓展的，M步就是完全背包

##### 该题的拓展题

#### 变式题：

##### 1.[使用最小花费爬楼梯](https://leetcode.cn/problems/min-cost-climbing-stairs/)

这个是变式，可以用来练手，递推和遍历很重要

##### 2.[打家劫舍](https://leetcode.cn/problems/house-robber/)

这个和上一题也是差不多的思路，但是初始化要注意，还有数组大小不一样时候的情况

##### 3.[ 删除并获得点数](https://leetcode.cn/problems/delete-and-earn/)

这个是打家劫舍的变式，中等题目，很适合思考一些拓展的方式

主要就是房屋的方式改变了，这是要考虑的

递归的方式仍然不变

```C
int sumsSize=0;
    for(int i=0;i<numsSize;i++) {
        sumsSize=fmax(sumsSize,nums[i]);
    }
    int sums[sumsSize+1];
    memset(sums,0,sizeof(sums));

    for(int i=0;i<numsSize;i++) {
        sums[nums[i]] += nums[i];
    }
```

### 矩阵

#### 基础题

##### 1.[不同路径](https://leetcode.cn/problems/unique-paths/)

矩阵类型的基础题

##### 2.[最小路径和](https://leetcode.cn/problems/minimum-path-sum/)

注意在力扣种矩阵的赋值为n=gridColSize[0];

#### 变式题

##### 1.[不同路径 II](https://leetcode.cn/problems/unique-paths-ii/)

哥们以后注意一下数组类型，longlongint有时候还是可能的

##### 2.[三角形最小路径和](https://leetcode.cn/problems/triangle/)

这个矩阵的赋值又和**2.最小路径和**不一样，看来是要看具体情况的

##### 3.[最大正方形](https://leetcode.cn/problems/maximal-square/)

这个最重要是知道状态转移

### 字符串

这个够复杂了，每次考虑都不一样。

#### 基础题

##### [1. 最长回文子串](https://leetcode.cn/problems/longest-palindromic-substring/)

虽然看起来像基础题，实际也花时间，遍历的过程需要注意，DP数组的值的含义，还有最终输出

##### [2.单词拆分](https://leetcode.cn/problems/word-break/)

这个有一个很重要的函数，C语言的函数，比较两个字符串是否相同

```
strncmp(s1,s2,length)
比较s1与s2的length长度内的值是否相同
s1>s2 返回大于0的值
s1<s2 返回小于0的值
相同返回0
```

还有一个很重要的用法：

```
S="babaaaddd"
一个字符串S，S+3
输出S为aaaddd
```

##### [3.最长回文子序列](https://leetcode.cn/problems/longest-palindromic-subsequence/)

遍历循序，从后面开始遍历能保证后边界。

##### [4.两个字符串的最小ASCII删除和](https://leetcode.cn/problems/minimum-ascii-delete-sum-for-two-strings/)

这个也是编辑距离的变式，只不过是换成输出ASCII码而已

#### 拓展题

##### [1.编辑距离](https://leetcode.cn/problems/edit-distance/)

这个最重要就算DP的初始化和定义，状态方程倒是可以推导

##### [2.不同的子序列](https://leetcode.cn/problems/distinct-subsequences/)

这个就是上面那个的变式，只不过这次是记录次数，不需要算删减次数

### 背包问题

**如果求组合数就是外层for循环遍历物品，内层for遍历背包**。

**如果求排列数就是外层for遍历背包，内层for循环遍历物品**。