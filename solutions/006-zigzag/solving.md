## 💡 해결 방법

Brute Force

양 끝에 닿으면 핑 퐁 일어나며 방향이 바뀐다.

## 해결

```java
class Solution {
    public String convert(String s, int numRows) {
        // 한줄은 그대로
        if(numRows==1) return s;

        // 이중 배열 대신 StringBuidler를 사용해 바로 문자열 연결함
        List<StringBuilder> rows = new ArrayList();

        for(int i =0; i<numRows; i++){
            rows.add(new StringBuilder());
        }
        // row의 순서를 맞춰주는 변수
        int ping = 0;
        // 방향 값
        boolean isPositive = false;
        // 문자열을 문자로 나누어 반복문 시작
        for(char c : s.toCharArray()){
            // 리스트 안에 있는 배열(지그재그의 순서)에 맞는 StringBuidler 안에 문자 삽입
             rows.get(ping).append(c);
            // 방향이 바귀어야 하는 순간
            if(ping == 0 || ping == numRows - 1){
                isPositive = !isPositive;
            }
            // 방향 전환 후 지그재그 row 순서 가감
            ping += isPositive ? +1 : -1;
        }

        // 리스트 안에 있는 StringBuidler를 합치기 위한 최종 빌더
        StringBuilder result = new StringBuilder();
        // rows 안에 있는 전체 빌더 합침
        for(StringBuilder row : rows){
            result.append(row);
        }
        // 문자열 반환
        return result.toString();
    }
}
```
