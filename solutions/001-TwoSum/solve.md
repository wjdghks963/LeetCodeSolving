## 💡 해결 방법

## 수도 코드

```
function twoSum(nums, target):
    for i from 0 to nums.length - 1:
        for j from i+1 to nums.length - 1:
            if nums[i] + nums[j] == target:
                return [i, j]  // 정답 반환
    return []  // 없으면 빈 배열 반환
```

## 해결

- **Brute Force**: O(N²) 시간 복잡도

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] arr = new int[2];

        for(int i =0; i<nums.length;i++){
            for(int j = i+1; j<nums.length; j++){
                if(nums[i]+nums[j]==target){
                    arr[0] = i;
                    arr[1] = j;
                }
            }
        }

        return arr;
    }
}
```

단순 이중 반복문을 사용해 두 개의 값을 각 위치에 삽입한다.

- **HashMap 사용**: O(N) 시간 복잡도

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // Hashmap 생성
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            // 차이를 찾을 수 있도록 첫값과 target을 뺀다.
            int complement = target - nums[i];
            // 만약 map 안에 해당값이 존재한다면 해당 값을 배열 반환
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            // 아니라면 array 안의 값을 키로 맵 안에 값을 넣는다.
            map.put(nums[i], i);
        }
        // return 이 없다면 빈배열 반환
        return new int[0];
    }
}
```
