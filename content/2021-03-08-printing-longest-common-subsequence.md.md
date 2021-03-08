---
title: Printing Longest Common Subsequence
date: 2021-03-08T06:04:32.810Z
cover: assets/logo-48.png
slug: dynamic-programming-classics-the-longest-common-subsequence
category: dp
tags:
  - dp
---
Problem Link: <https://www.hackerrank.com/challenges/dynamic-programming-classics-the-longest-common-subsequence/problem>

```cpp
vector<int> longestCommonSubsequence(vector<int> a, vector<int> b) {
    int n = a.size();
    int m = b.size();
    int arr[n+1][m+1];
    vector<int> ans;
    for(int i=0; i<=n; i++) {
        for(int j=0; j<=m; j++) {
            if(i==0 || j==0) {
                arr[i][j] = 0;
            } else if(a[i-1] == b[j-1]) {
                arr[i][j] = arr[i-1][j-1]+1;
            } else {
                arr[i][j] = max(arr[i-1][j], arr[i][j-1]);
            }
        }
    }
    int i=n;
    int j=m;
    while(i>0 && j>0) {
        if(arr[i][j] == arr[i-1][j]) {
            i--;
        } else if(arr[i][j] == arr[i][j-1]) {
            j--;
        } else if(arr[i][j] == (arr[i-1][j-1]+1)) {
            ans.push_back(b[j-1]);
            i--;
            j--;
        } 
    }
    reverse(ans.begin(), ans.end()); 
    return ans;
}

```