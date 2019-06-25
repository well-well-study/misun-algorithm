``` java
package More.Programers.Greedy;

import java.util.Stack;

public class BigNumber {

  public static void main(String[] args) {
    String number = "4177252841";
    int k = 4;
    System.out.println(solution(number, k));

  }

  public static String solution(String number, int k) {
    char[] result = new char[number.length() - k];
    Stack<Character> stack = new Stack<Character>();

    for (int i = 0; i < number.length(); i++) {
      char c = number.charAt(i);
      while (!stack.isEmpty() && stack.peek() < c && k-- > 0) {
        stack.pop();
      }
      stack.push(c);
    }
    for (int i = 0; i < result.length; i++) {
      result[i] = stack.get(i);
    }
    return new String(result);
  }
}
