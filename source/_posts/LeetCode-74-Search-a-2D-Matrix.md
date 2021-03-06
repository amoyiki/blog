---
title: '[LeetCode]74. Search a 2D Matrix'
date: 2016-12-21 10:42:05
categories: "Algorithms"
tags:
- 学习
---
### 问题描述 ###
在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

### 解题思路 ###
一开始打算用二分查找的方式，将二维数组划分成两部分，递归判断。实际写出来的时候就发现，二维数组并不好去判断值。后来在网上看到一个更好的方法。
>将二维数组转化成二维平面，将target值从第一行的最后一个值开始查找，小于就往左边移动，大于就往下面移动。

| | | | |
| :---: |:---:| :---:| :---:|
|1|3|5|7|
|10|11|16|20|
|23|30|34|50|
<!-- more -->
### 具体代码 ###
**python**
```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        if matrix is None or len(matrix)==0:
            return False
        row = len(matrix)
        col = len(matrix[0])
        i=col-1
        j=0
        while(i>=0 and j<row):
            if matrix[j][i] == target:
                return True
            elif matrix[j][i] > target:
                i = i - 1
            elif matrix[j][i] < target:
                j = j + 1
        return False
```
**java**
```java
public class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix==null || matrix.length==0 || matrix[0].length==0) 
            return false;
        int i = 0;
        int j = matrix[0].length - 1;
        while (i <= matrix.length - 1 && j >= 0) {
            if (target == matrix[i][j]) {
                return true;
            } else if (target < matrix[i][j]) {
                j--;
            } else if (target > matrix[i][j]) {
                i++;
            }
        }
        return false;
    }
}
```
