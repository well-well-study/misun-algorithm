#### 테스트 완벽 통과 X

``` java
package More.Programers.Greedy;

import java.util.ArrayList;
import java.util.List;

public class JoyStick {

  public static void main(String[] args) throws Exception {
    String name = "JAN";
    System.out.println(Integer.toString(solution(name)));
  }

  public static int solution(String name) {
    int alphaCount = 0;
    int answer = 0;
    int countA = 0;
    int countL = 0;
    int countR = 0;
    int length = name.length();
    char subStr;

    List<Character> nameArr = new ArrayList<Character>();
    for (int i = 0; i < length; i++) {
      nameArr.add(name.charAt(i));
    }

    for (int i = 0; i < length; i++) {
      subStr = nameArr.get(i);
      if (subStr != 65) {
        alphaCount += (subStr <= 77) ? (subStr - 65) : (91 - subStr);
      }
    }

    for (int i = 0; i < length; i++) {
//      subStr = nameArr.get(i);
//      if (subStr != 65) {
//        answer += (subStr <= 77) ? (subStr - 65) : (91 - subStr);
//      }

      if (i < length - 2) {
        if (nameArr.get(i + 1) > 65)
          answer++;
      }

      if (i < length - 2) {
        if (nameArr.get(i + 1) == 65) {
          for (int j = length - 1; nameArr.get(j) == 65; j--) {
            countL++;
          }
          countL = countL + 1;
        }
      }

      if (i < length - 2) {
        if (nameArr.get(i + 1) == 65) {
          for (int j = length - 1; nameArr.get(j) == 65; j--) {
            countR++;
          }
        }
      }

      if (countL > countR && (countL > 0 || countR >0))
        answer = answer + countR;
      if (countL == countR && (countL > 0 || countR >0))
        answer = answer + countL;
      if (countL < countR && (countL > 0 || countR >0))
        answer = answer + countL;

    }
    answer = answer + alphaCount + 1;
    return answer;
  }
}

// n 78
/*
 *  1. 현재 글자를 움직일 필요가 있는지 (0)
 *  2. 있다면 26중에 어느쪽으로 움직이는게 좋을지 (0)
 *  3. 오른쪽으로 움직일 필요가 있는지
 *  4. 오른쪽 글자가 움직일 필요가 있는지
 *  5. 없다면 왼쪽으로 가는게 나은지
 *  6. 없다면 오른쪽으로 가는게 나은지
 * *
*/
