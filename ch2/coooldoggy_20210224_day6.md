#### 합성수 

2부터 n-1까지의 정수 중에 나누어떨어지는 정수가 하나 이상 존재하는 수 

### Q8 메서드 dayOfYear를 변수 i와 days 없이 구현하세요. while문을 사용하세요.

```java
package ch02.practice;

import java.util.Scanner;

public class ch02_q8 {
    // 각 달의 일 수
    static int[][] mdays = {
            {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31},	// 평년
            {31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}	// 윤년
    };

    // 서기 year년은 윤년인가? (윤년：1／평년：0)
    static int isLeap(int year) {
        return (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) ? 1 : 0;
    }


    // 서기 y년 m월 d일의 그 해 경과 일수를 구함
   static int dayOfYear(int y, int m, int d) {
        int isLeap = isLeap(y);
        while(m > 1){
            --m;
            d += mdays[isLeap][m - 1];
        }
        return d;
    }

    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);
        int retry;							// 다시 한 번?

        System.out.println("그 해 경과 일 수를 구합니다.");

        do {
            System.out.print("년：");  int year  = stdIn.nextInt();	// 년
            System.out.print("월：");  int month = stdIn.nextInt();	// 월
            System.out.print("일：");  int day   = stdIn.nextInt();	// 일

            System.out.printf("그 해 %d일째입니다.\n", dayOfYear(year, month, day));

            System.out.print("한번 더 할까요? (1.예／0.아니오）：");
            retry = stdIn.nextInt();
        } while (retry == 1);
    }
}

```



### Q9 y년 m월 d일의 그 해 남은 일 수 (12월 31일 이면 0, 12월 30일이면 1)를 구하는 아래 메서드를 작성하세요.

```java
  static int leftDayOfYear(int y, int m, int d){
        int total;
        if(isLeap(y) == 0){
            total = 365;
        }else{
            total = 366;
        }
       return total - dayOfYear(y, m, d);
    }
```



### Q10 시력분포를 오른쪽처럼 그래프로 출력하도록 바꾸어 프로그램을 작성하세요. 기호 문자 *를 사람 수만큼 반복하여 나타내세요.

```java
package ch02.practice;

import java.util.Scanner;

public class ch02_q10 {
    static final int VMAX = 21;		// 시력 분포(0.0에서 0.1 단위로 21개）

    static class PhyscData {
        String name;				// 이름
        int    height;				// 키
        double vision;				// 시력

        // 생성자
        PhyscData(String name, int height, double vision) {
            this.name 	= name;
            this.height = height;
            this.vision = vision;
        }
    }

    // 키의 평균값을 구함
    static double aveHeight(ch02_q10.PhyscData[] dat) {
        double sum = 0;

        for (int i = 0; i < dat.length; i++)
            sum += dat[i].height;

        return sum / dat.length;
    }

    // 시력 분포를 구함
    static void distVision(ch02_q10.PhyscData[] dat,
                           int[] dist) {
        int i = 0;

        dist[i] = 0;
        for (i = 0; i < dat.length; i++)
            if (dat[i].vision >= 0.0 && dat[i].vision <= VMAX / 10.0)
                dist[(int)(dat[i].vision * 10)]++;
    }

    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);

        ch02_q10.PhyscData[] x = {
                new ch02_q10.PhyscData("박현규", 162, 0.3),
                new ch02_q10.PhyscData("함진아", 173, 0.7),
                new ch02_q10.PhyscData("최윤미", 175, 2.0),
                new ch02_q10.PhyscData("홍연의", 171, 1.5),
                new ch02_q10.PhyscData("이수진", 168, 0.4),
                new ch02_q10.PhyscData("김영준", 174, 1.2),
                new ch02_q10.PhyscData("박용규", 169, 0.8),
        };
        int[] vdist = new int[VMAX];					// 시력 분포

        System.out.println("■ 신체검사 리스트 ■");
        System.out.println(" 이름         키       시력");
        System.out.println("---------------");
        for (int i = 0; i < x.length; i++)
            System.out.printf("%-8s%3d%5.1f\n",
                    x[i].name, x[i].height, x[i].vision);

        System.out.printf("\n평균 키：%5.1fcm\n", aveHeight(x));

        distVision(x, vdist);							// 시력 분포를 구함

        System.out.println("\n시력 분포");
        for (int i = 0; i < VMAX; i++)
            System.out.printf("%3.1f~：%s\n", i / 10.0, returnStar(vdist[i]));
    }
    
    public static String returnStar(int num){
        StringBuilder builder = new StringBuilder();
        for (int i = 0; i < num; i ++){
            builder.append("*");
        }
        return builder.toString();
    }
}

```



### Q11 오른쪽처럼 서기 년월일을 필드로 갖는 클래스를 만드세요. 다음과 같이 생성자와 메서드를 정의해야 합니다. 

- 생성자(주어진 날짜로 설정) YMD(int y, int m, int d)
- n일 뒤의 날짜를 반환 YMD after(int n)
- n일 앞의 날짜를 반환 YMD before(int n)

```java
package ch02.practice;


import java.util.Scanner;

public class ch02_q11 {
     int year;
     int month;
     int day;

    static int[][] mdays = {
            {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31},    // 평년
            {31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}    // 윤년
    };

    static int isLeap(int year) {
        return (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) ? 1 : 0;
    }

    public static void main(String[] args) {
        Scanner stdIn = new Scanner(System.in);

        System.out.print("날짜를 입력하세요.\n");
        System.out.print("년：");
        int y = stdIn.nextInt();
        System.out.print("월：");
        int m = stdIn.nextInt();
        System.out.print("일：");
        int d = stdIn.nextInt();
        ch02_q11 date = new ch02_q11(y, m, d);

        System.out.print("몇 일 앞/뒤의 날짜를 구할까요?：");
        int n = stdIn.nextInt();

        ch02_q11 d1 = date.after(n);
        System.out.printf("%d일 뒤의 날짜는 %d년 %d월 %d일입니다.\n", n, d1.year, d1.month, d1.day);

//        ch02_q11 d2 = date.before(n);
//        System.out.printf("%d일 앞의 날짜는 %d년 %d월 %d일입니다.\n", n, d2.y, d2.m, d2.d);
    }

    ch02_q11(int y, int m, int d) {
        this.year = y;
        this.month = m;
        this.day = d;
    }

    // n일 뒤의 날짜를 반환
    ch02_q11 after(int n) {
        ch02_q11 temp = new ch02_q11(this.year, this.month, this.day);
        if (n < 0)
            return (before(-n));

        temp.day += n;

        while (temp.day > mdays[isLeap(temp.year)][temp.month - 1]) {
            temp.day -= mdays[isLeap(temp.year)][temp.month - 1];
            if (++temp.month > 12) {
                temp.year++;
                temp.month = 1;
            }
        }
        return temp;
    }

    // n일 앞의 날짜를 반환
    ch02_q11 before(int n) {
        ch02_q11 temp = new ch02_q11(this.year, this.month, this.day);
        if (n < 0)
            return (after(-n));

        temp.day -= n;

        while (temp.day < 1) {
            if (--temp.month < 1) {
                temp.year--;
                temp.month = 12;
            }
            temp.day += mdays[isLeap(temp.year)][temp.month - 1];
        }
        return temp;
    }
}

```

