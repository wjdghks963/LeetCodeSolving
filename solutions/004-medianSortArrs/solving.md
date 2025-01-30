## 💡 해결 방법

이진탐색 사용

중앙값이란

가운데로 반 나눈 후 왼쪽의 최대값, 오른족의 최소값을 합한 후

짝수 : / 2 한 값
홀수 : 왼쪽에서 가장 큰 값

## 해결

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        // 항상 nums1이 더 작은 배열이 되도록 보장
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.length;
        int n = nums2.length;
        int left = 0, right = m;
        int partX, partY;

        while (left <= right) {
            // nums1의 절반을 나눔
            partX = (left + right) / 2;
            // nums2에서 대응되는 절반 위치
            partY = (m + n + 1) / 2 - partX;

            // 경계를 벗어나지 않도록 처리
            // nums1의 왼최대 / 오최소 구함
            int maxLeftX = (partX == 0) ? Integer.MIN_VALUE : nums1[partX - 1];
            int minRightX = (partX == m) ? Integer.MAX_VALUE : nums1[partX];
            // nums2의 왼최대 / 오최소 구함
            int maxLeftY = (partY == 0) ? Integer.MIN_VALUE : nums2[partY - 1];
            int minRightY = (partY == n) ? Integer.MAX_VALUE : nums2[partY];

            // 올바른 중앙값을 찾은 경우
            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                // 짝수라면
                if ((m + n) % 2 == 0) {
                    // 왼쪽 최대 값 중 큰 값 + 오른쪽 최소 값 중 작은 값
                    return (Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2.0;
                } else {
                    // 홀수라면 왼쪽 최대값 중 큰 값
                    return Math.max(maxLeftX, maxLeftY);
                }
            }

            // nums1의 왼쪽 부분이 너무 큼
            if (maxLeftX > minRightY) {
                // 왼쪽으로 이동
                right = partX - 1;
            } else { //왼쪽 부분이 너무 큼
                // 오른쪽 이동
                left = partX + 1;
            }
        }

        throw new IllegalArgumentException("Input arrays are not sorted properly.");
    }
}
```
