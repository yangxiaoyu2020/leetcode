[链接]()
#### 解题思路
- 132 举个栗子
```txt
2入
3碰到了他
3入
2出
1碰到2
说明1比2 小
i < j < k
nums[i] < nums[k] < nums[j] 。
这样就形成了
```
#### 代码
```java
class Solution {
    public boolean find132pattern(int[] nums) {
        // 只是返回是不是，应该加入多少个这样dfs来计算
        // 单调栈来处理这类问题
        // 总结下
        boolean res = false;
        int max3 = Integer.MIN_VALUE;
        if (nums.length < 3) return res;
        LinkedList<Integer> stack = new LinkedList();
        for (int i = nums.length-1; i >= 0; i--) {
            int num = nums[i];
            if (num < max3) {
                res = true;
                return res;
            }
            else {
                while (!stack.isEmpty() && num > stack.peek()) {
                    max3 = stack.peek();
                    stack.removeFirst();
                    // System.out.println(max3);
                }
                if (num > max3) {
                    stack.addFirst(num);
                }
            }

        }
        return res;


    }
}
```
