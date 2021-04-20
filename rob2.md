[链接](https://leetcode-cn.com/problems/house-robber-ii/solution/dp-huan-xing-da-jie-by-user5713q-iqn4/)

### 解题思路
java
分两种情况 1 包含头
          2 包含尾
### 代码

```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length <= 2) return nums.length % 2 == 0? Math.max(nums[1], nums[0]): nums[0];
        return Math.max(rob1(Arrays.copyOfRange(nums, 0, nums.length-1)), rob1(Arrays.copyOfRange(nums, 1, nums.length)));

    }   

    private int rob1(int[] nums) {
        int[] dp = new int[nums.length+1];
        dp[0] = 0;
        dp[1] = nums[0];
        for (int i = 2; i < nums.length + 1; i++) {
            dp[i] = Math.max(dp[i-1], dp[i-2]+ nums[i-1]);
        }
        return dp[nums.length];
    }

}
```
