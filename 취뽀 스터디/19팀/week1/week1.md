# 19팀 취뽀 스터디 1주차 (2023.10.07 ~ 2023.10.12)

---
## 일시
### 23.10.12.목(21~22시)
- 프로그래머스 라이브코딩 주제 : 추억 점수 [LV.1]
- 면접 대비 주제 : 데이터베이스 (예상질문 및 모범답안, 꼬리질문 논의 및 공유)
- 참여자: 조현수, 최병호, 김상훈
        
---
## 기술면접 질문
### 1. 트랜잭션이 무엇인지 설명해주세요. <br>

데이터베이스의 상태를 변화시키는 하나의 논리적 작업 단위를 의미.<br>
논리적인 작업의 쿼리 개수와 관계 없이 트랜잭션으로 묶어놓은 <br>
작업 단위 전체가 모두 적용되거나 아무것도 적용되지 않음을 보장.

### 1.1 - 트랜잭션의 특징은 무엇이 있을까요? <br>

트랜잭션의 특징은 앞글자를 따서 ACID라고 부름.<br>
*원자성(Atomicity)* 은 트랜잭션을 구성하는 연산 전체가 모두 정상적으로 실행되거나 모두 취소되어야 한다는 특성입니다.<br>
*일관성(Consistency)* 은 트랜잭션이 실행되기 전과 후에 데이터베이스가 일관된 상태를 유지해야 한다는 것을 의미합니다.<br>
*고립성(Isolation)* 은 여러 트랜잭션이 동시에 실행될때, 각 트랜잭션은 서로에게 영향을 주지 않고 독립적으로 실행되어야 함을 의미합니다.<br>
*지속성(Durability)* 는 트랜잭션이 성공적으로 완료된 후, 그 결과가 데이터베이스에 영구적으로 저장되어야 한다는 것을 의미합니다.(장애나 오류가 나더라도)

### 1.2 - 트랜잭션의 상태는 어떤 것들이 있을까요? <br>

*Active* : 트랜잭션이 실행 중인 상태<br>
*Fail*: 트랜잭션 실행에 오류가 발생해 중단된 상태<br>
*Aborted*: 트랜잭션이 비정상적으로 종료되어 롤백을 수행하는 상태 <br>
*Partitially Commit*: 트랜잭션이 마지막 연산까지 실행했지만, Commit 연산이 실행되기 직전의 상태.<br>
*Committed*: 트랜잭션이 성공적으로 종료되어 커밋 연산을 실행한 후의 상태.<br>

### 1.3 - 트랜잭션 격리 수준들에 대해 설명해주세요. <br>

동시에 여러 트랜잭션이 처리될 때, 트랜잭션끼리 얼마나 서로 고립되어 있는지를 나타내는 것을 트랜잭션의 격리 수준이라고 함.<br> 
즉, 특정 트랜잭션이 다른 트랜잭션에 변경한 데이터를 볼 수 있도록 허용할 지 말지를 결정하는 것.<br>
*Read Uncomitted(dirty read 발생)* : 가장 낮은 격리 수준, 한 트랜잭션에서의 변경 내용이 아직 커밋되지 않았더라도, 다른 트랜잭션에서 그 변경내용을 조회할 수 있음.<br>
*Read Committed(non-repeatable-read 발생)* : 한 트랜잭션에서의 변경 내용이 커밋된 후에만, 다른 트랜잭션에서 그 변경 내용을 조회 가능.(대부분의 RDBMS)<br>
*Repeatable Read(phantom Read)* : 트랜잭션 동안 동일한 쿼리를 여러번 실행하더라도, 조회하는 내용이 항상 동일함을 보장하는 격리수준.<br>
*Serializable* : 여러 트랜잭션이 동일한 레코드에 동시 접근할 수 없는 격리수준.

### 참고 <br>

Dirty Read란 한 트랜잭션이 아직 커밋되지 않은 다른 트랜잭션의 변경을 읽는것.(롤백될 데이터를 읽을수도 있음)<br>
Non Repeatable Read는 한 트랜잭션 내에서 같은 쿼리를 두번 수행했을때, 두 쿼리의 결과가 서로 다른것.(다른 트랜잭션이 수정 또는 삭제한 경우)<br>
Phantom Read는 한 트랜잭션내에서 같은 쿼리를 두번수행했을 때, 처음과 다음 조회 사이에 새로운 데이터 항목이 삽입되거나 삭제되어 결과의 행 수가 변경되는 현상.<br>

트랜잭션 연산 중, Commit과 Rollback에 대해 설명해주세요.
Commit 연산은 트랜잭션의 모든 변경 사항을 데이터베이스에 영구적으로 저장하는 연산이고(커밋 이후 취소 불가), 롤백은 트랜잭션의 변경 사항을 취소하고, 데이터베이스를 트랜잭션이 시작되기 전의 상태로 되돌리는 연산입니다.

이 연산들을 통해 트랜잭션의 원자성을 보장하고, 데이터의 무결성과 일관성을 유지할 수 있음.

---
## 라이브 코딩
https://school.programmers.co.kr/learn/courses/30/lessons/176963

- 조현수
```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        Map<String, Integer> map = IntStream.range(0, name.length)
                .boxed()
                .collect(Collectors.toMap(idx -> name[idx], idx -> yearning[idx]));

        return Arrays.stream(photo)
                .mapToInt(people -> Arrays.stream(people)
                        .filter(map::containsKey)
                        .mapToInt(map::get)
                        .sum())
                .toArray();
    }
}
```

- 최병호
```java
import java.util.*;

class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        int[] answer = new int[photo.length];
        // 추억 점수를 저장할 변수를 HashMap으로 정의합니다.
        HashMap<String, Integer> yearnPoint = new HashMap<>();
        
        // 추억점수와 인물을 yearnPoint에 담습니다.
        for(int i = 0; i < name.length; i++) {
            yearnPoint.put(name[i], yearning[i]);
        }
        
        
        for(int i = 0; i < photo.length; i++) {
            for(int j = 0; j < photo[i].length; j++){ // photo의 길이가 100 이하이므로 O(N^2)를 해도 상관 없습니다.
                if(yearnPoint.get(photo[i][j]) != null) { // null인 경우 대비
                    answer[i] += yearnPoint.get(photo[i][j]); // 사진의 그리움 점수를 추가합니다.
                }
            }
        }
        return answer;
    }
} 
```

- 김상훈
```java
import java.util.*;
class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        int[] answer = new int[photo.length];
        HashMap<String,Integer> hm = new HashMap<>();
        for(int i = 0 ; i < name.length ; i++) hm.put(name[i],yearning[i]);
        for(int i = 0 ; i < photo.length ; i++){
            for(int j = 0 ; j< photo[i].length ; j++){
                answer[i]+=hm.getOrDefault(photo[i][j],0);
            }
        }
        return answer;
    }
}
```
---
### 2주차 계획 - 23.10.19.목(21시~)
- 프로그래머스 라이브코딩
- 면접 대비 주제 : 네트워크 (예상질문 및 모범답안, 꼬리질문 논의 및 공유)
    
