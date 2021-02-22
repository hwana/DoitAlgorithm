# 배열

주사 : 배열의 요소를 하나씩 차례로 살펴보는 과정 (스캔)



### Q1 키뿐만 아니라 사람 수도 난수로 생성하도록 실습 2-5를 수정하여 프로그램을 작성하세요.

```java
import java.util.Random;

public class ch02_q1 {

    public static void main(String[] args) {
        Random rand = new Random();

        int num = rand.nextInt(10);
        System.out.println("키의 최댓값을 구합니다.");
        System.out.println("사람 수 : " + num);

        int[] height = new int[num];

        System.out.println("키 값을 아래와 같습니다.");

        for (int i =0; i < num; i++){
            height[i] = 100 + rand.nextInt(90);
            System.out.println("height[" + i + "] : " + height[i]);
        }

        System.out.println("최댓값은 "+ maxof(height) + "입니다.");
    }

    static int maxof(int[] a){
        int max = a[0];
        for (int i =1; i < a.length; i++){
            if (a[i] > max){
                max = a[i];
            }
        }
        return max;
    }
}

```



### Q2 오른쪽처럼 배열 요소를 역순으로 정렬하는 과정을 하나하나 나타내는 프로그램을 작성하세요.

```java
public class ch02_q2 {
    public static void main(String[] args) {
        int[] x = {5, 10, 73, 2, -5, 42};
        reverse(x);
        System.out.println("역순 정렬을 마쳤습니다.");
    }

    static void swap(int[] a, int idx1, int idx2){
        int t = a[idx1];
        a[idx1] = a[idx2];
        a[idx2] = t;
    }

    static void reverse(int[] a){
        for (int i =0; i < a.length/2; i++){
            printArray(a);
            System.out.println();
            swap(a, i, a.length - i - 1);
            System.out.println("a[" + i + "]와 a[" + (a.length - i - 1 )+ "]를 교환합니다.");
        }
    }

    static void printArray(int[] a){
        for (int i =0; i < a.length; i++){
            System.out.print(a[i] + " ");
        }
    }
}
```



### Q3 배열 a의 모든 요소의 합계를 구하여 반환하는 메서드를 작성하세요

```java
static int sumOf(int[] a){
        int sum = 0;
        for (int i = 0; i < a.length; i ++){
            sum += a[i];
        }
        return sum;
    }
```



### Q4 배열 b의 모든 요소를 배열 a에 복사하는 메서드 copy를 작성하세요.

```java
public class ch02_q3 {
    static void copy(int[] a, int[] b) {
        int length = a.length <= b.length ? a.length : b.length;
        for (int i =0; i< length; i++){
            a[i] = b[i];
        }
    }

    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);

        System.out.print("배열 a의 요솟수 ：");
        int numa = stdIn.nextInt();
        int[] a = new int[numa];
        for (int i = 0; i < numa; i++) {
            System.out.print("a[" + i + "] : ");
            a[i] = stdIn.nextInt();
        }

        System.out.print("배열 b의 요솟수는 ：");
        int numb = stdIn.nextInt();
        int[] b = new int[numb];
        for (int i = 0; i < numb; i++) {
            System.out.print("b[" + i + "] : ");
            b[i] = stdIn.nextInt();
        }

        copy(a, b);

        System.out.println("배열 b의 모든 요소를 배열 a에 복사.");
        for (int i = 0; i < numa; i++)
            System.out.println("a[" + i + "] = " + a[i]);
    }
}

```



### Q5 배열b의 모든 요소를 배열 a에 역순으로 복사하는 메서드 rcopy를 작성하세요.

```java

public class ch02_q3 {

    static void rcopy(int [] a, int [] b){
        int length = a.length <= b.length ? a.length : b.length;
        for (int i =0; i< length; i++){
           a[i] = b[length - i - 1];
        }
    }

    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);

        System.out.print("배열 a의 요솟수 ：");
        int numa = stdIn.nextInt();
        int[] a = new int[numa];
        for (int i = 0; i < numa; i++) {
            System.out.print("a[" + i + "] : ");
            a[i] = stdIn.nextInt();
        }

        System.out.print("배열 b의 요솟수는 ：");
        int numb = stdIn.nextInt();
        int[] b = new int[numb];
        for (int i = 0; i < numb; i++) {
            System.out.print("b[" + i + "] : ");
            b[i] = stdIn.nextInt();
        }

        rcopy(a, b);

        System.out.println("배열 b의 모든 요소를 배열 a에 복사.");
        for (int i = 0; i < numa; i++)
            System.out.println("a[" + i + "] = " + a[i]);
    }
}
```

