## 💡 해결 방법

Set
슬라이딩 윈도우

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();

        int maxLength = 0;
        int start = 0;

        for(int i =0; i < s.length(); i++){

            char cur = s.charAt(i); // 현재 char 값
            while(set.contains(cur)){ // set 안에 해당 char 값이 있다면
                set.remove(s.charAt(start)); // 시작에 해당하는 값 제거
                start++; // 시작 값 ++
            }

            set.add(cur);

            maxLength = Math.max(maxLength, i-start+1); // 최대 값 갱신


        }
    return maxLength;

    }
}
```
