---
title: Longest Common Prefix in an Array
date: 2021-03-06T08:52:32.520Z
cover: assets/logo-48.png
slug: longest-common-prefix-in-an-array
category: strings
tags:
  - strings
---
Given an array of **N** strings, find the longest common prefix among all strings present in the array.

**Example 1:**

```
Input:
N = 4
arr[] = {geeksforgeeks, geeks, geek,
         geezer}
Output: gee
Explanation: "gee" is the longest common
prefix in all the given strings.
```

**Example 2:**

```
Input: 
N = 2
arr[] = {hello, world}
Output: -1
Explanation: There's no common prefix
in the given strings.
```

\
**Your Task:**\
You don't need to read input or print anything. Your task is to complete the function **longestCommonPrefix()** which takes the string array **arr**\[] and its size **N** as inputs and **returns** the longest common prefix common in all the strings in the array. If there's no prefix common in all the strings, return "-1".

\
**Expected Time Complexity:** O(N*max(|arri|)).\
**Expected Auxiliary Space:** O(max(|arri|)) for result.

\
**Constraints:**\
1<=N<=103\
1<=|arri|<=103

**Solution:**

```cpp
string longestCommonPrefix (string arr[], int N) {
    int count=0, minn=INT_MAX;
    string s="";
    for(int i=0; i<N; i++) {
        if(minn>arr[i].length()) {
            minn = arr[i].length();
        }
    }
    char ch;
    for(int i=0; i<minn; i++) {
        int flag =0;
        char c = arr[0][i];
        for(int j=0; j<N; j++) {
            ch = arr[j][i];
            if(arr[j][i]!=c) {
                flag = 1;
                break;
            }
        }
        if(flag == 0) {
            s += ch;
            count++;
        }
    }
    if(count == 0) {
        return "-1";
    }
    return s; 
}
```