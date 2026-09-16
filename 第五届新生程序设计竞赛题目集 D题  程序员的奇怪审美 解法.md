```java
//第五届新生程序设计竞赛题目集 D题  程序员的奇怪审美 解法
package P25;

import java.util.Scanner;

public class P25 {
    public static void main(String[] args) {
        //分析题意可知总共排列在遵循以下6种规则
        int change = 0;
        int min;
        char[][] List= {
                {'R', 'G', 'B'}, {'R', 'B', 'G'}, {'G', 'R', 'B'}, {'G', 'B', 'R'}, {'B', 'R', 'G'}, {'B', 'G', 'R'}
        };
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入灯笼的个数");
        int num = sc.nextInt();
        System.out.println("请输入灯笼的颜色分别是");
        String color = sc.next();
        StringBuilder sb_res = new StringBuilder();
        for (int k = 0; k < color.length(); k++) {
            if (color.charAt(k) != List[0][k % 3]) {
                change++;
                sb_res.append(List[0][k % 3]);
            } else {
                sb_res.append(color.charAt(k));
            }
        }
        min = change;
        for (int i = 1; i < List.length; i++) {
            change = 0;
            StringBuilder sb = new StringBuilder();
            for (int j = 0; j < color.length(); j++) {
                if (color.charAt(j) != List[i][j % 3]) {
                    change++;
                    sb.append(List[i][j % 3]);
                } else {
                    sb.append(color.charAt(j));
                }
            }
            //求出change的最小值
            if (min > change) {
                min = change;
                sb_res = sb;
            }
        }
        System.out.println("最小的次数为:" + min);
        System.out.println("样式为:" + sb_res.toString());

    }
}
```