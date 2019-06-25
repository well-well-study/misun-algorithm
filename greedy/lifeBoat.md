``` java
package More.Programers.Greedy;

import java.util.Arrays;

public class LifeBoat {

  public static void main(String[] args) throws Exception {
    int[] people = {70, 80, 50};
    int limit = 100;
    System.out.println((Integer.toString(solution(people, limit))));
  }

  public static int solution(int[] people, int limit) {
    int answer = 0;
    int j = people.length - 1;
    Arrays.sort(people);

    for (int i = 0; i <= j; i++) {
      answer++;
      while (j > i && people[i] + people[j--] > limit) {
        answer++;
      }
    }

    return answer;
  }
}
