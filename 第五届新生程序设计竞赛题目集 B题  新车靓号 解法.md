```java
import java.util.Scanner;

public class Test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int inputNum = sc.nextInt();
        int[] arr = new int[inputNum];
        for (int i = 0; i < inputNum; i++) {
            int level = 5;
            String plate = sc.next();
            judgePlate(plate);
            char temp = plate.charAt(0);
            for (int j = 1; j < plate.length(); j++) {
                boolean flag = judgeTemp(temp);
                if (flag) {
                    if (plate.charAt(j) >= '0' && plate.charAt(j) <= '9') {
                        level--;
                    } else {
                        temp = 'A';
                    }
                } else {
                    if (plate.charAt(j) >= 'A' && plate.charAt(j) <= 'Z') {
                        level--;
                    } else {
                        temp = '0';
                    }
                }
            }
            arr[i] = level;
        }
        //遍历arr
        printArr(arr);
    }
    public static void judgePlate(String plate) {
        if (plate.length() != 5) {
            throw new IllegalArgumentException("车牌长度有误!");
        }
    }
    public static void printArr(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
    public static boolean judgeTemp(char temp) {
        boolean flag = true;
        if (temp >= '0' && temp <= '9') {
            return true;
        } else {
            return false;
        }
    }
}

```