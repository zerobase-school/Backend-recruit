# 19팀 취뽀 스터디 6주차 (2023.11.20 ~ 2023.11.26)

---
## 일시
### 23.11.23.목(20:30~22시)
- 프로그래머스 라이브코딩 주제 : [LV2. 연속된 부분 수열의 합 - DFS](https://school.programmers.co.kr/learn/courses/30/lessons/178870)
- 참여자: 조현수, 김상훈, 김동역, 장진영

---

## 라이브 코딩 주제 및 코드

### 풀이 (김상훈, 장진영, 김동역, 조현수)
```java
import java.util.*;
class Solution {
    public int[] solution(int[] sequence, int k) {
        int[] answer = new int[]{0,0};
        int sequenceLen = sequence.length;
        int start = 0;
        int end = 0;
        int total = 0;
        int minLen = 1000001;
        while(end < sequenceLen) {
            total += sequence[end];
            while(total >= k) {
                if(total == k && end-start < minLen){
                    minLen = end - start;
                    answer[0] = start;
                    answer[1] = end;
                }
                total -= sequence[start];
                start ++;
            }
            end++;
        }
        
        return answer;
    }
}
```

---

### 8주차 계획 - 23.11.30.목(20시~)
- 프로그래머스 라이브코딩 (주제 : 슬라이딩윈도우)
- 면접 대비 주제 : 네트워크
    
