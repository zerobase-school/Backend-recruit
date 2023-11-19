# 19팀 취뽀 스터디 6주차 (2023.11.13 ~ 2023.11.19)

---
## 일시
### 23.11.16.목(20:30~22시)
- 프로그래머스 라이브코딩 주제 : [LV2. 이모티콘 할인행사 - DFS](https://school.programmers.co.kr/learn/courses/30/lessons/150368)
- 면접 대비 주제 : 스프링부트 (예상질문 및 모범답안, 꼬리질문 논의 및 공유)
- 참여자: 조현수, 최병호, 김상훈, 김동역, 장진영
        
---
## 기술면접 질문

### 1. 김동역 - ORM과 JPA
**ORM이란?** <br>
ORM은 Object Relational Mapping의 줄임말로, 자바와 같은 객체지향 언어에서의 객체와 RDB(Relational Database, 관계형 데이터베이스)의 테이블을 자동으로 매핑하는 방법이다.<br>
ORM을 이용하면 쿼리문을 작성이 아닌 코드로 데이터를 조작할 수 있다.<br>
**ORM의 장점** <br>
쿼리를 객체지향적으로 조작할 수 있다.<br>
쿼리문을 작성하는 양이 아주 많이 줄어든다.<br>
즉, 재사용 및 유지보수가 편리하다. (객체지향을 따르므로)<br>
데이터베이스에 대한 종속성이 줄어든다. (예를 들어, MySQL을 사용하던 데이터베이스를 MariaDB로 교체한다고 했을 때, 약간 바뀌는 모든 쿼리문을 교체할 필요도 없고 그만큼 에러가 발생할 위험도 줄어든다.)<br>
**ORM의 단점** <br>
복잡한 쿼리를 요구하는 경우 코드로 구현하기 어려우며 성능 문제가 발생할 수 있다.<br>
객체의 관점과 데이터베이스의 관계의 관점에는 차이가 있어서 혼동이 발생할 수 있다.<br>
**JPA** <br>
JPA는 Java Persistence API를 의미하며, 자바의 ORM 기술 표준으로 채택된 인터페이스이다. ORM이 개념이라면 JPA는 조금 더 구체적인 명세라고 생각하면 되겠다.<br>
JPA는 내부적으로 JDBC를 사용하는데, 개발자가 JDBC를 활용하여 구현하면 SQL에 의존하게 되어 효율이 떨어진다. JPA는 이 문제점을 보완하여 개발자 대신 요구하는 기능에 맞는 SQL을 생성하고 데이터베이스를 조작하여 객체와 데이터베이스를 이어준다.<br>
이를 기반으로 구현한 것 중 가장 많이 사용되는 것이 하이버네이트(Hibernate) 이고, 스프링 부트에서는 이 하이버네이트의 기능을 더욱 편하게 사용하도록 구현된 Spring Data JPA를 활용할 수 있다.<br>
예상질문 - 영속성 컨텍스트에 대해 설명하시오.<br>
JPA에서 영속성 컨텍스트는 엔티티를 영구 저장하는 환경이라는 뜻입니다.<br> 
영속성 컨텍스트는 애플리케이션과 DB 사이에서 객체를 보관하는 가상의 DB 역할을 하며, 엔티티 매니저(EntityManager)를 통해 엔티티를 저장하거나 조회하면 엔티티 매니저는 영속성 컨텍스트에 엔티티를 보관하고 관리하게 됩니다.<br>
영속성 컨텍스트를 통해 자료의 생성, 삭제, 수정 등을 관리하게 됩니다.

### 2. 조현수 - IOC란 무엇인가요??

OC란 프로그램의 제어 흐름을 코드 내에서(개발자) 직접 제어한 것이 아니라 외부에서 관리하는 것<br>
스프링 애플리케이션에서는 빈의 생성과 의존관계 설정 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당<br>
이를 스프링 컨테이너가 코드 대신 오브젝트에 대한 제어권을 가지고 있다고 해서 IOC 컨테이너라고도 함<br>
**꼬리질문- IOC 컨테이너란 무엇인가요?**
스프링 애플리케이션에서는 객체의 생성과 관계 설정,<br>
사용, 제거 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당하는데, 이를 IOC 컨테이너라고 함<br>
IOC 컨테이너 장점은 스프링 애플리케이션의 객체(빈)을 IOC 컨테이너가 관리해줌으로써<br>
개발자의 부담이 줄고 비즈니스 로직에 집중할 수 있다는 장점이 있습니다.<br>
스프링 컨테이너는 빈들을 인스턴스 형식으로 관리함, 즉 한번 생성 후 여러 클라이언트가 하나의 같은 객체 인스턴스를 공유함<br>
따라서 상태를 유지하게 끔 설계하면 안됨. restful이 아닌 stateless로 설계해야 함<br>
특정 클라이언트에 의존적인 필드나, 특정 클라이언트가 값을 변경할 수 있는 필드가 존재하면 안됨<br>

### 3. 장진영 - DI에 대해서 설명해주세요.
객체가 직접 의존하는 객체를 생성하거나 관리하는 것이 아니라, 외부에서 의존 객체를 주입받도록 하는 것<br>
그렇다면 의존 객체를 주입받도록 하면 어떤 장점이있는지 설명해주세요.<br>
객체 간의 결합도를 낮추고 코드의 재사용성과 유지보수성을 향상<br>
스프링 DI(Dependency Injection)는 객체 간의 의존성을 외부에서 관리하여 객체 간 결합도를 낮추고 유연하고 확장 가능한 구조를 만들 수 있도록 도와주며<br>
주로 역제어(Inversion of Control, IoC) 컨셉과 함께 사용되며, 스프링 프레임워크에서는 이를 통해 객체의 생성, 생명 주기, 의존성 해결 등을 효과적으로 관리<br>
**IoC에 대해 설명해주세요.**
객체를 생성하고 관리하고 의존성을 관리해주는 컨테이너이며, 컨테이너가 빈 설정 정보를 바탕으로 자동으로 DI를 해준다.

### 4. 김상훈 - DAO, DTO 그리고 VO
DAO는 Data Access Object, DTO는 Data Transfer Object, VO는 Value Object의 약자입니다.<br>
DAO는 DB의 data에 접근하기 위한 객체입니다.<br>
CRUD 작업을 수행합니다.<br>
Service와 DB를 연결합니다.<br>
Repository package를 DAO라고 부를 수도 있습니다.<br>
DTO는 계층간 데이터 교환을 위해 사용하는 객체로, 로직을 가지지 않는 순수한 데이터 객체입니다.<br>
Getter/Setter만 가집니다.<br>
Service나 Controller에 데이터를 보낼 때 사용됩니다.<br>
엔티티를 DTO형태로 변환한 뒤 사용합니다.<br>
VO는 Read-Only 속성을 가진 객체입니다.<br>
Getter만 가지고 Setter를 가질 수 없습니다.<br>
특정 값 자체를 표현합니다.<br>
불변성을 보장해야 신뢰성이 있습니다.<br>
**꼬리질문  - DTO와 VO의 차이점은 뭔가요?** <br>
DTO는 인터턴스 개념이라면 VO는 리터럴 값 개념입니다.<br>
동등성의 측면에서 DTO는 필드 값이 같아도 같은 객체가 아닐 수 있지만(주소 값이 다른 경우) VO는 필드 값이 같다면 같은 객체입니다.<br>
DTO는 Getter/Setter만 가지지만 VO는 Getter/Setter 외의 로직이 존재할 수도 있습니다.<br>
**꼬리질문 2 - VO의 동등성 비교는 어떻게 해야 하나요?**
주소값을 비교하는 경우의 문제점을 방지하기 위해서 hashcode()와 equals()를 재정의하여 필드 값이 같다면 같은 객체로 인식될 수 있도록 해주어야 합니다.<br>
---> DI와 IoC에 대해 연결지어서 생각<br>

---

## 라이브 코딩 주제 및 코드

### 김상훈 풀이
```java
import java.util.Arrays;

public class Solution {
    int[] max;

    public int[] solution(int[][] users, int[] emoticons) {
        max = new int[users.length + 1];
        Arrays.fill(max, Integer.MIN_VALUE);
        int[] usedMoney = new int[users.length];
        boolean[] gotService = new boolean[users.length];

        dfs(users, emoticons, usedMoney, gotService, 0);

        for (int i = max.length - 1; i >= 0; i--) {
            if (max[i] >= 0) {
                return new int[]{i, max[i]};
            }
        }
        return new int[]{0, 0};
    }

// idx가 끝에 도달하면 gotService를 돌며 몇번 사람이 서비스를 등록하고 몇번 사람이 이모티콘을 구매했는지 확인
// 서비스 등록자라면 count를, 이모티콘 구매자라면 totalMoney를 usedMoney만큼 증가
    public void dfs(int[][] users, int[] emoticons, int[] usedMoney, boolean[] gotService, int idx) {
        if (idx == emoticons.length) {
            int totalMoney = 0;
            int count = 0;
            for (int i = 0; i < gotService.length; i++) {
                if (!gotService[i]) {
                    totalMoney += usedMoney[i];
                } else {
                    count++;
                }
            }
            if (max[count] < totalMoney) {
                max[count] = totalMoney;
            }
            return;
        }

// 이자율 10부터 40까지 증가하면서 전체 탐색, 이전 결과가 반영되지 않도록 기존 array들을 깊은 복사
        for (int i = 10; i <= 40; i += 10) {
            int price = emoticons[idx] * (100 - i) / 100;
            int[] tmpUsedMoney = Arrays.copyOf(usedMoney, usedMoney.length);
            boolean[] tmpGotService = Arrays.copyOf(gotService, gotService.length);

            for (int j = 0; j < users.length; j++) {
                if (tmpGotService[j]) {
                    continue;
                }
                if (users[j][0] > i) {
                    continue;
                }
                if (users[j][1] > price + tmpUsedMoney[j]) {
                    tmpUsedMoney[j] += price;
                    continue;
                }
                tmpGotService[j] = true;
            }
            dfs(users, emoticons, tmpUsedMoney, tmpGotService, idx + 1);
        }
    }
}
```

### 김동역 풀이
```java
class Solution {
    
    static int plusMember = 0;
    static int total = 0;
    
    public void dfs(int[] arr, int index, int[][] users, int[] emoticons) {
        int[] discount = {10, 20, 30, 40};
        
        // 한 조합이 완성되면 이모티콘 구입 계산
        if (index == arr.length) {
            calculate(arr, users, emoticons);
            return;
        }
        
        // 경우 뻗어나가기
        // 할인율은 중복이 가능한 중복순열
        for (int i=0; i<discount.length; i++) {
            arr[index] = discount[i];
            dfs(arr, index + 1, users, emoticons);
        }
    }
    
    public void calculate(int[] arr, int[][] users, int[] emoticons) {
        
        int plusCount = 0;
        int tempTotal = 0;
        
        for(int[] user : users) {
            int discount = user[0];
            int price = user[1];
            int sum = 0;
            
            // 할인율을 만족하는 모든 이모티콘 구입
            for (int i=0;i<arr.length; i++) {
                if (arr[i] >= discount) {
                    sum += (emoticons[i] * (100 - arr[i])) / 100;
                }
            }
            
            // 비용 넘어가면 이모티콘 플러스 가입
            if (sum >= price) {
                plusCount++;
            } else {
                tempTotal += sum;
            }  
        }
        
        // 플러스 가입자 수(목표 1) 비교
        // 그 다음으로 판매액(목표 2) 비교
        if (plusCount > plusMember) {
            plusMember = plusCount;
            total = tempTotal;
            return;
        } else if (plusCount == plusMember) {
            total = Math.max(total, tempTotal);
        }
    }
    
    public int[] solution(int[][] users, int[] emoticons) {
        int[] arr =new int[emoticons.length];
        
        // 모든 경우의 수를 계산하기 위한 DFS
        dfs(arr, 0, users, emoticons);
        
        return new int[]{plusMember, total};
    }
}
```

### 조현수 풀이
```java
class Solution {
    // 가능한 할인율 배열
    static int[] discountRates = {10, 20, 30, 40};
    // 최대 가입자 수
    static int maxOfSubscribe;
    // 최대 판매 금액
    static int maxOfCost;

    
    public int[] solution(int[][] users, int[] emoticons) {
        // 이모티콘 수
        int emoticonLength = emoticons.length;
        // 할인율 배열 초기화
        int[] discounts = new int[emoticonLength];

        // 할인율 배열 초기값 설정
        for (int i = 0; i < emoticonLength; i++) {
            discounts[i] = discountRates[0];
        }

        // 계산 시작
        calculate(0, emoticonLength, discounts, users, emoticons);

        // 결과 반환
        return new int[]{maxOfSubscribe, maxOfCost};
    }

    // 가능한 할인율 조합 계산 함수
    public void calculate(int index, int emoticonLength, int[] discounts, int[][] users, int[] emoticons) {
        // 할인율 배열이 모두 설정되면
        if (index == emoticonLength) {
            // 가입자 수와 판매 금액 계산
            int subscribe = 0;
            int cost = 0;

            // 모든 사용자에 대해 처리
            for (int[] user : users) {
                int userDiscountRate = user[0];
                int userMaxCost = user[1];
                int totalCost = 0;

                // 사용자별로 구매 가능한 이모티콘 금액 계산
                for (int i = 0; i < emoticonLength; i++) {
                    if (discounts[i] >= userDiscountRate) {
                        totalCost += emoticons[i] / 100 * (100 - discounts[i]);
                    }
                }

                // 구매 조건 확인 후 가입자 수 및 판매 금액 갱신
                if (totalCost >= userMaxCost) {
                    subscribe++;
                } else {
                    cost += totalCost;
                }
            }

            // 최적의 결과 확인 및 업데이트
            if (subscribe > maxOfSubscribe) {
                maxOfSubscribe = subscribe;
                maxOfCost = cost;
            } else if (subscribe == maxOfSubscribe) {
                maxOfCost = Math.max(maxOfCost, cost);
            }
            return;
        }

        // 가능한 모든 할인율에 대해 조합 탐색
        for (int rate : discountRates) {
            discounts[index] = rate;
            //재귀
            calculate(index + 1, emoticonLength, discounts, users, emoticons);
        }
    }
}
```
---

### 7주차 계획 - 23.11.23.목(20시~)
- 프로그래머스 라이브코딩 (주제 : 슬라이딩윈도우)
- 면접 대비 주제 : 네트워크
    
