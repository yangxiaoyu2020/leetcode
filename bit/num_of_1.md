[链接](https://leetcode-cn.com/problems/number-of-1-bits/solution/java-wei-yun-suan-by-user5713q-0dum/)


### java 位运算
**yangxiaoyu**
- 发布于 几秒前
0
#### 解题思路
- 这个解释清楚了
```java
1111 & 1110 = 1110
1110 & 1101 = 1100
1100 & 1011 = 1000
1000 & 0111 = 0000
```

**代码**
```Java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int res = 0;
        while (n != 0) {
            res += 1;
            n &= (n-1);
        }
        return res;
    }
}
```
