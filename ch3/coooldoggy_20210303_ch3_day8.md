### Q3 요솟수가 n인 배열 a에서 key와 일치하는 모든 요소의 인덱스를 배열 idx의 맨 앞부터 순서대로 저장하고 일치한 요솟수를 반환하는 메서드를 작성하세요. 예를 들어 요솟수가 8인 배열a의 요소가 {1,9,2,9,4,6,7,9}이고 key가 9이면 배열 idx에 {1,3,7}을 저장하고 3을 반환합니다.

```java
package ch03.practice;

import java.util.Arrays;
import java.util.Objects;
import java.util.Scanner;
import java.util.concurrent.LinkedTransferQueue;
import java.util.function.Predicate;

public class ch03_q3 {
    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);
        System.out.print("요솟수：");
        int num = stdIn.nextInt();
        int[] x = new int[num]; // 요솟수 num인 배열
        int[] y = new int[num]; // 요솟수 num인 배열

        for (int i = 0; i < num; i++) {
            System.out.print("x[" + i + "]：");
            x[i] = stdIn.nextInt();
        }
        System.out.print("찾는 값："); // 키 값을 입력 받음
        int ky = stdIn.nextInt();

        int count = searchIdx(x, num, ky, y);

        if (count == 0)
            System.out.println("그 값의 요소가 없습니다.");
        else
            for (int i = 0; i < count; i++)
                System.out.println("그 값은 " + "x[" + y[i] + "]에 있습니다.");
    }

    static int searchIdx(int [] a, int n, int key, int[] idx){
        int j = 0;
        for (int i = 0; i < a.length; i ++){
            if (key == a[i]){
                idx[j] = i;
                j++;
            }
        }
        int temp[] = new int[j];
        for (int i = 0; i < temp.length; i++){
            temp[i] = idx[i];
        }

        idx = temp;
        return idx.length;
    }
}

```



### Q4 오른쪽처럼 이진 검색의 과정을 자세히 출력하는 프로그램을 작성하세요. 각 행의 맨 왼쪽에 현재 검색하고 있는 요소의 인덱스를 출력하고, 검색 범위의 맨 앞 요소에 <-, 맨 끝 요소 위에 ->, 현재 검색하고 있는 중앙 요소 위에 +를 출력하도록 하세요.

```java
package ch03.practice;

import java.util.Scanner;

public class ch03_q4 {
    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);

        System.out.print("요솟수：");
        int num = stdIn.nextInt();
        int[] x = new int[num]; // 요솟수 num인 배열

        System.out.println("오름차순으로 입력하세요.");

        System.out.print("x[0]："); // 맨 앞 요소를 읽어 들임
        x[0] = stdIn.nextInt();

        for (int i = 1; i < num; i++) {
            do {
                System.out.print("x[" + i + "]：");
                x[i] = stdIn.nextInt();
            } while (x[i] < x[i - 1]); // 하나 앞의 요소보다 작으면 다시 입력
        }

        System.out.print("찾는 값："); // 키 값을 입력 받음
        int ky = stdIn.nextInt();

        int idx = binSearch(x, num, ky); // 배열 x에서 값이 ky인 요소를 검색

        if (idx == -1)
            System.out.println("그 값의 요소가 없습니다.");
        else
            System.out.println(ky + "은 x[" + idx + "]에 있습니다.");
    }

    private static int binSearch(int[] x, int num, int ky) {
        System.out.print(" " + "|");
        for (int i = 0; i < x.length; i ++){
            System.out.print(" " + i + " ");
        }
        System.out.println();
        System.out.println("-+---------------------");
        StringBuilder arrayBuilder = new StringBuilder();
        for (int i = 0; i < x.length; i ++){
            arrayBuilder.append(String.format("%d ", x[i]));
        }

        int pl = 0;			// 검색 범위의 첫 인덱스
        int pr = num - 1;		// 검색 범위의 끝 인덱스

        do {
            int pc = (pl + pr) / 2;		// 중앙 요소의 인덱스
            System.out.println(printArrow(x.length, pc));
            System.out.printf("%d| %s", pc, arrayBuilder);
            System.out.println();
            if (x[pc] == ky)
                return pc;				// 검색 성공!
            else if (x[pc] < ky)
                pl = pc + 1;			// 검색 범위를 뒤쪽 절반으로 좁힘
            else
                pr = pc - 1;			// 검색 범위를 앞쪽 절반으로 좁힘
        } while (pl <= pr);
        return -1;
    }

    static String printArrow(int length, int mid){
        StringBuilder builder = new StringBuilder();
        builder.append("  <-");
        for (int i = 1; i <= mid; i ++){
            builder.append(" ");
        }

        builder.append(" +");

        for (int i = mid; i < length; i ++){
            builder.append(" ");
        }

        builder.append("->");
        return builder.toString();
    }
}

```



### Q5 우리가 살펴본 이진 검색 알고리즘 프로그램은 검색할 값과 같은 값을 갖는 요소가 하나 이상일 경우 그 요소 중에서 맨 앞의 요소를 찾지 못합니다. 예를 들어 아래 그림의 배열에서 7을 검색하면 중앙에 위치하는 a[5]를 검색합니다. 맨 앞의 요소를 찾는 binSearchX 메서드를 작성해 보세요

```java

```

