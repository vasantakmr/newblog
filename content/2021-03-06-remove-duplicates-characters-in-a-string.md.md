---
title: Remove Duplicates characters in a String
date: 2021-03-06T06:55:25.088Z
cover: assets/logo-48.png
slug: remove-duplicates
category: strings
tags:
  - strings
---
Problem Link: <https://practice.geeksforgeeks.org/problems/remove-duplicates/0>

Given a string without spaces, the task is to remove duplicates from it.

**Note:** The original order of characters must be kept the same. 

**Example 1:**

```
Input: S = "zvvo"
Output: "zvo"
Explanation: Only keep the first
occurrence
```

**Example 2:**

```
Input: S = "gfg"
Output: gf
Explanation: Only keep the first
occurrence
```

**Your task:**\
Your task is to complete the function **removeDups()** which takes a single string as input and returns the string. You need not take any input or print anything. 

**Expected Time Complexity:** O(|s|)\
**Expected Auxiliary Space:** O(constant)

**Constraints:**\
1 <= |S| <= 105\
S conatins lowercase english alphabets

**Solution:**

```cpp
string removeDups(string S) 
{
    int arr[26] = {0};
    string s="";
    for(int i=0; i<S.length(); i++) {
        if(arr[S[i]-'a']==0) {
            s += S[i];
            arr[S[i]-'a']++;
        }
    }
    return s;
}
```