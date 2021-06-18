[题目链接](https://leetcode-cn.com/problems/implement-strstr/solution/java-bao-li-jia-kmp-by-user5713q-etr3/)


### 解题思路
KMP 关键在于 构建next数组
next数组就是构建一个 关于 pattern 的 前后 序列的一个 前后缀的一个 记忆数组
next[0] = -1
next的长度是pattern + 1;

next[pattern.lenght()]

### 代码

```java
class Solution {
    public int strStr(String haystack, String needle) {
        if (haystack.length() == 0 && needle.length() == 0) return 0;
        if (needle.length() == 0) return 0;
        if (haystack.length() < needle.length()) return -1;
        int index = 0;
        for (int i = 0; i < haystack.length(); i++) {
            if (haystack.charAt(i) == needle.charAt(index) && (i + needle.length()) <= haystack.length()) {
                if (haystack.substring(i, i + needle.length()).equals(needle)) {
                    return i;
                }
            }
        }
        return -1;
    }
}
```java

```java

// KMP 必须要啃下来的东西
class Solution {
    public int strStr(String haystack, String needle) {
        if ((needle.length() == 0 && haystack.length() == 0) || needle.length() == 0) return 0;;
        if (needle.length() > haystack.length()) return -1;
        int[] next = buildNext(needle);
        int i = 0;
        int j = 0;
        while (i < haystack.length()) {
            if (haystack.charAt(i) != needle.charAt(j)) {
                j = next[j];
                if (j == -1) {
                    i++;
                    j = 0;
                }
            }
            else {
                i++;
                j++;
                if (j == needle.length()) return i - j;
            }
        }
        return -1;




    }

    private int[] buildNext(String pattern) {
        int[] next = new int[pattern.length()+1];
        next[0] = -1;
        int i = 2;
        int k = 0;
        while (i <= pattern.length()) {
            if (k == -1 || pattern.charAt(i-1) == pattern.charAt(k)) {
                next[i] = k + 1;
                k++;
                i++;

            }
            else {
                k = next[k];
            }
        }
        return next;

    }
}



```
