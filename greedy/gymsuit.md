``` java
package More.Programers.Greedy;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class GymSuit {

  public static void main(String[] args) {
    int n = 3;
    int[] lost = {1, 2};
    int[] reserve = {2, 3};

    System.out.println(Integer.toString(solution(n, lost, reserve)));
  }

  public static int solution(int n, int[] lost, int[] reserve) {
    int answer = 0;

    Arrays.sort(lost);
    Arrays.sort(reserve);

    answer = n - lost.length;

    List<Integer> lostArr = new ArrayList<Integer>();
    List<Integer> reserveArr = new ArrayList<Integer>();

    for (int i = 0; i < lost.length; i++) {
      lostArr.add(lost[i]);
    }

    for (int i = 0; i < reserve.length; i++) {
      reserveArr.add(reserve[i]);
    }

    for (int i : lostArr) {
      if (reserveArr.contains(i)) {
        reserveArr.remove((Integer) i);
        answer++;
      } else if (reserveArr.contains(i + 1)) {
        reserveArr.remove((Integer) (i + 1));
        answer++;
      } else if (reserveArr.contains(i - 1)) {
        reserveArr.remove((Integer) (i - 1));
        answer++;
      }
    }
    return answer;
  }
}

/*
 * 1. 2 <= n <= 30
 * 2. 1 <= lost.length <= n
 * 3. 1 <= reserve.length <= n
 * */

/*
 * 1. reserve를 하고 있는 학생의 번호와 lost를 하고있는 학생의 번호가 1개 차이나는지 검사한다.
 * 2. answer에 reserve 배열의 수를 대입한다.
 * 3. 그런 것이 있다면, reserve에서 삭제하고
 * 4. answer에 ++ 해준다.
 * */

