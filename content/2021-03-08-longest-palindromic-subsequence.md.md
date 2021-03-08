---
title: Longest Palindromic Subsequence
date: 2021-03-08T09:32:02.589Z
cover: assets/logo-48.png
slug: longest-palindromic-subsequence
category: dp
tags:
  - dp
---
Problem Link: <https://www.interviewbit.com/problems/longest-palindromic-subsequence/>

```cpp
int Solution::solve(string A) {
    int len = A.length();
    int arr[len][len];
    for(int i=0; i<len; i++) {
        arr[i][i] = 1;
    }
    for(int sl=2; sl<=len; sl++) {
        for(int i=0; i<len-sl+1; i++) {
            int j = i+sl-1;
            if(A[i] == A[j] && sl == 2) {
               arr[i][j] = 2; 
            } else if(A[i] == A[j]) {
                arr[i][j] = 2 + arr[i+1][j-1];
            } else {
                arr[i][j] = max(arr[i][j-1], arr[i+1][j]);
            }
        }
    }
    return arr[0][len-1];
}

```