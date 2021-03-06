# LeetCode: 598. 范围求和 II

[TOC]

## 1、题目描述



给定一个初始元素全部为 **0**，大小为 m*n 的矩阵 **M** 以及在 **M** 上的一系列更新操作。

操作用二维数组表示，其中的每个操作用一个含有两个**正整数 a** 和 **b** 的数组表示，含义是将所有符合 **0 <= i < a** 以及 **0 <= j < b** 的元素 **M[i][j]** 的值都**增加 1**。

在执行给定的一系列操作后，你需要返回矩阵中含有最大整数的元素个数。

**示例 1:**

```
输入: 
m = 3, n = 3
operations = [[2,2],[3,3]]
输出: 4
解释: 
初始状态, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

执行完操作 [2,2] 后, M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

执行完操作 [3,3] 后, M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

M 中最大的整数是 2, 而且 M 中有4个值为2的元素。因此返回 4。
```

**注意:**

1. m 和 n 的范围是 [1,40000]。
2. a 的范围是 [1,m]，b 的范围是 [1,n]。
3. 操作数目不超过 10000。



## 2、解题思路

​	实际上，每一次操作，都是对0-a,0-b之间的数进行增加，那么就很好办了，我们只需要找到所有的操作中，最小的a,b就可以了

​	讲真，这道题很无趣

```c
int maxCount(int m, int n, int** ops, int opsRowSize, int opsColSize) {
    int row = INT32_MAX;
    int col = INT32_MAX;

    for (int i = 0; i < opsRowSize; i++) {
        if (ops[i][0] < row) {
            row = ops[i][0];
        }
        if (ops[i][1] < col) {
            col = ops[i][1];
        }
    }

    row = row < m ? row : m;
    col = col < n ? col : n;

    return row * col;
}
```

