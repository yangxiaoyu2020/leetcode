## 题解
* 最大值的猜想，

 * O(n) 的时间复杂度


```java

class Solution {Â
    public int maxSubArray(int[] nums) {
        int res = Integer.MIN_VALUE;
        if (nums.length == 0) return res;

        int preSum = 0;
        for (int i = 0; i < nums.length; i++) {
            if (preSum + nums[i] >= nums[i]) {
            preSum += nums[i];
            }
            else if (preSum + nums[i] < nums[i]) {
                preSum = nums[i];
            }
            res = Math.max(preSum, res);

        }
        return Math.max(preSum, res);


    }
}
```
