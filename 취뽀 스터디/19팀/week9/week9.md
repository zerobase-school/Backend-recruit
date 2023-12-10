# 19팀 취뽀 스터디 9주차 (2023.12.04 ~ 2023.12.10)

---
## 일시
### 23.12.07.목(20:30~22시)
- 프로그래머스 라이브코딩 주제 : [LV2. 주차요금계산](https://school.programmers.co.kr/learn/courses/30/lessons/92341)
- 참여자: 조현수, 김상훈, 장진영, 최병호

---

## 라이브 코딩 주제 및 코드

### 풀이 (김상훈, 장진영, 최병호, 조현수)
```java
import java.util.*;

// 차 이름 및 입/출차 시간 (정렬할꺼니까 comparable 구현)
class Car implements Comparable<Car> {
    int num;
    int time;

    public Car(int num, int time) {
        this.num = num;
        this.time = time;
    }

    @Override
    public int compareTo(Car o) {
        return this.num - o.num;
    }
}

class Solution {
    public int[] solution(int[] fees, String[] records) {
        // 입장 차량 관리 맵
        Map<Integer, Integer> entryTimeMap = new HashMap<>();
        // 주차시간 관리 맵
        Map<Integer, Integer> parkingTimeMap = new HashMap<>();
        
        // 정렬위한 리스트
        List<Car> cars = new ArrayList<>();
        
        int defaultTime = fees[0];
        int defaultFee = fees[1];
        int unitTime = fees[2];
        int unitFee = fees[3];

        /**
        레코드 배열 순회하면서 차가 인이면 입차 관리맵에 넣음
        만약 출차이면 입차 관리맵에 있는 값 불러와서 시간계산해서 시간관리맵에 삽입
        시간은 분으로 모두 환산해서 입/출차 차이계산해서 저장
        */ 
        for (String record : records) {
            String[] log = record.split(" ");
            String[] time = log[0].split(":");
            int currentTime = Integer.parseInt(time[0]) * 60 + Integer.parseInt(time[1]);
            int carNumber = Integer.parseInt(log[1]);

            if (log[2].equals("IN")) {
                entryTimeMap.put(carNumber, currentTime);
                // System.out.println("in! : " + carNumber);
            } else {
                int parkedTime = currentTime - entryTimeMap.get(carNumber);
                parkingTimeMap.put(carNumber, parkingTimeMap.getOrDefault(carNumber, 0) + parkedTime);
                entryTimeMap.remove(carNumber);
                // System.out.println("out! : " + carNumber);
            }
        }
        
        //입차만 하고 출차없는애들 계산
        for (int carNumber : entryTimeMap.keySet()) {
            int currentTime = 23 * 60 + 59; // 23 : 59 분 -> 분 
            int parkedTime = currentTime - entryTimeMap.get(carNumber);
            parkingTimeMap.put(carNumber, parkingTimeMap.getOrDefault(carNumber, 0) + parkedTime);
        }

        // 시간맵을 사용해 금액 계산해서 리스트에 Car 객체에 담아 저장
        for (int carNumber : parkingTimeMap.keySet()) {
            int totalParkingTime = parkingTimeMap.get(carNumber);
            int totalFee = defaultFee;

            if (totalParkingTime > defaultTime) {
                totalParkingTime -= defaultTime;
                totalFee += (totalParkingTime + unitTime - 1) / unitTime * unitFee;
            }

            cars.add(new Car(carNumber, totalFee));
        }

        //리스트 저장
        Collections.sort(cars);

        int[] result = new int[cars.size()];

        for (int i = 0; i < cars.size(); i++) {
            result[i] = cars.get(i).time;
        }

        //반환
        return result;
    }
}
```

---

### 8주차 계획 - 23.12.14.목(20시~)
- 프로그래머스 라이브코딩 (주제 : BFS)
    
