#### 解题思路
 - 好像还可以提速

```txt
执行用时：
15 ms
, 在所有 Java 提交中击败了
8.66%
的用户
代码
```
```java

class ParkingSystem {
    HashMap<Integer, Integer> parkMap;

    public ParkingSystem(int big, int medium, int small) {
        this.parkMap = new HashMap();
        parkMap.put(1, big);
        parkMap.put(2, medium);
        parkMap.put(3, small);
    }

    public boolean addCar(int carType) {
        if (parkMap.get(carType) <= 0 ) {
            return false;
        }
        parkMap.put(carType, parkMap.get(carType)-1);
        return true;

    }
}


/**
 * Your ParkingSystem object will be instantiated and called as such:
 * ParkingSystem obj = new ParkingSystem(big, medium, small);
 * boolean param_1 = obj.addCar(carType);
 */
 ```

作者：user5713Q
- 又看到我自己了，以后打算用这个做密码。。。lol

[链接：https://leetcode-cn.com/problems/design-parking-system/solution/java-hashmapshi-xian-qi-shi-yong-shu-zu-4d5w5/](https://leetcode-cn.com/problems/design-parking-system/solution/java-hashmapshi-xian-qi-shi-yong-shu-zu-4d5w5/)
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
