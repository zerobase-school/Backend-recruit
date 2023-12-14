# 19팀 취뽀 스터디 10주차 (2023.12.11 ~ 2023.12.17)

---
## 일시
### 23.12.14.목(9:00~9:45)
- 프로그래머스 라이브코딩 주제 : [골드4. 소트 게임](https://www.acmicpc.net/problem/1327)
- 참여자: 조현수, 김상훈

---

## 라이브 코딩 주제 및 코드

### 풀이 (김상훈, 조현수)
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class N1327 {

    static int cnt = Integer.MAX_VALUE;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] NK = br.readLine().split(" ");
        int N = Integer.parseInt(NK[0]);
        int K = Integer.parseInt(NK[1]);
        int[] input = Arrays.stream(br.readLine().split(" ")).mapToInt(Integer::parseInt).toArray();
        int[] answer = Arrays.stream(input).sorted().toArray();
        bfs(input, answer, 0, K, 0);
        if (cnt == Integer.MAX_VALUE) {
            System.out.println(-1);
        } else {
            System.out.println(cnt);
        }

    }

    public static void bfs(int[] input, int[] answer, int idx, int K, int count) {
        if (Arrays.equals(input, answer)) {
            cnt = Math.min(cnt, count);
            return;
        }
        if (idx >= input.length - 1) return;
        bfs(sort(input, idx, K), answer, idx + 1, K, count + 1);
        bfs(input, answer, idx + 1, K, count + 1);
    }

    public static int[] sort(int[] input, int idx, int K) {
        int[] tmp = input.clone();
        int limit = Math.min(idx + K, input.length);
        for (int i = idx; i < limit; i++) {
            input[i] = tmp[limit - i + idx - 1];
        }
        return input;
    }
}
김상훈
```
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    static int n;
    static int k;
    static int[] items;
    static int[] criteria;
    static int cnt;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] nums = br.readLine().split(" ");
        n = Integer.parseInt(nums[0]);
        k = Integer.parseInt(nums[1]);

        items = new int[n];
        int idx = 0;
        for(String s : br.readLine().split(" ")) {
            items[idx++] = Integer.parseInt(s);
        }

        criteria = Arrays.copyOf(items, items.length);
        Arrays.sort(criteria);

        move(0);

    }
    private static void move(int idx){
        if(Arrays.equals(criteria, items)){
            System.out.println(cnt);
            return;
        }
        if(idx > items.length-k){
            cnt = 0;
            move(idx+1);
        }
        if(items[idx] > items[idx+1]){
            swap(idx);
            cnt++;
        }
    }
    private static void swap(int idx){
        int[] temp = Arrays.copyOfRange(items, idx, idx + k);
        int j = temp.length-1;
        for(int i = idx ; i < idx+k ; i++){
            items[i] = temp[j--];
        }
    }
}
조현수
```

---

### 11주차 계획 - 23.12.21.목(21시~)
- 백준 라이브코딩 (주제 : BFS)
    
