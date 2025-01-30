## 💡 해결 방법

1. ListNode 특성 사용
2. 반 올림 값 담아 놓는 변수 생성

## 해결

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0); // 리스트의 시작을 가리키는 더미(dummy) 노드
        ListNode result = head;
        int carry = 0; // 올림 10 이상의 수를 다음 계산에 받을 때 사용

        while(l1 != null | l2 != null | carry != 0){
            int sum = 0; // 합산

            if(l1 != null){
                sum += l1.val;
                l1 = l1.next;
            }

            if(l2 != null){
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10; // 몫 계산
            head.next = new ListNde(sum % 10 ); // 나머지를 head의 다음 노드에 넣음
            head = head.next; // 헤드는 다음노드로 이동함
        }
        return result.next; // 더미 이후의 리스트를 반환
    }
}
```

첫 head는 더미 값으로 사용하며 다음 값을 연결 시키기 위한 변수로서 사용됨

result 는 head를 계속 참조 하며 Link 되는 list를 물고 있음

따라서 최종값은 첫 더미를 버린 다음 리스트들을 반환함
