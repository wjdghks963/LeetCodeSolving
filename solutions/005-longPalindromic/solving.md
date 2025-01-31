## 💡 해결 방법

확장 중심 방법

한칸씩 이동하며 양옆을 확인하고 start, end를 지속적으로 업데이트하며 지나간다

## 해결

```java
class Solution {
    public String longestPalindrome(String s) {
        if(s.length()== 1) return s;

        // 회문 시작점
        int start = 0;
        // 회문 종료점
        int end = 0;


        for(int i =0; i<s.length(); i++){
            // 'bab' 홀수 회문
            int odd = findLen(s, i, i);
            // 'bb' 짝수 회문
            int even = findLen(s, i, i+1);
            // 중 제일 큰 값
            int len = Math.max(odd, even);

            // 만약 회문이 내가 가지고 있는 길이보다 크다면 업데이트
            if (len > (end - start)) {
                //왼쪽으로 (len - 1) / 2만큼 확장됨
                start = i - (len - 1) /2;
                //오른쪽으로 len / 2 만큼 확장됨
                end = i + (len/2);
            }
        }
        return s.substring(start, end + 1);

    }


    // 조건(회문)에 맞는 재귀문
    public int findLen(String s, int start, int end){
        // 회문의 조건문
        while (start >= 0 && end < s.length() && s.charAt(start) == s.charAt(end)) {
                start--;
                end++;
        }
        // 길이값 반환
        return end-start-1;

    }


}
```
