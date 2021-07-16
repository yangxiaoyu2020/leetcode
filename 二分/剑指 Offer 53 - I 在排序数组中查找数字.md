## 解题思路：
- 不管怎么华丽的代码
  - 首先找到要找的 index
  - 然后两步走： 向左 向右  要是维空间的话就四面八方去找


```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length==0)return 0;
        int res = 0;
        int left = 0;
        int right = nums.length;
        while (left < right) {
            int mid = (left + right) >>> 1;
            if (nums[mid] == target) {
                left = mid;
                break;
            }
            else if (nums[mid] > target) {
                right = mid;
            }
            else {
                left = mid + 1;
            }
        }
        if (left < 0 || left >= nums.length || nums[left] != target) return res;
        // System.out.print(left);
        right = left;
        while ((left >= 0 && nums[left] == target) || (right < nums.length && nums[right] == target )) {
            if (left == right) {
                res++;
                left--;
                right++;
            }
            else if (left >= 0 && nums[left] == target) {
                res++;
                left--;
            }
            else if (right < nums.length && nums[right] == target) {
                right++;
                res++;
            }
        }
        return res;

    }
}
```
