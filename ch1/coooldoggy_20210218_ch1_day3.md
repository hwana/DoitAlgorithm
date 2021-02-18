## 구조적 프로그래밍

### 드모르간 법칙

각 조건을 부정하고 논리곱을 논리합으로, 논리합을 논리곱으로 바꾸고 다시 전체를 부정하면 원래의 조건과 같다는 법칙 

#### Q12 오른쪽과 같이 위쪽과 왼쪽에 곱하는 수가 있는 곱셈표를 출력하는 프로그램을 작성하세요. 

```java
public class ex01_12 {
	public static void main(String[] args) {
		String horizontal = "|";
		
		System.out.print("   "+horizontal);
		for (int i = 1; i <= 9; i++)
			System.out.printf("%3d", i);
		System.out.println("\n---+---------------------------");

		for (int i = 1; i <= 9; i++) {
			System.out.printf("%2d |", i);
			for (int j = 1; j <= 9; j++)
				System.out.printf("%3d", i * j);
			System.out.println();
		}
	}
}
```

%d 숫자 대입 %3d인데 2자릿수 넣으면 1자리는 공백 들어감 



#### Q13 곱셈이 아니라 덧셈을 출력하는 프로그램을 작성하세요 

````java
public class ex01_13 {
	public static void main(String[] args) {
		String horizontal = "|";

		System.out.print("   " + horizontal);
		for (int i = 1; i <= 9; i++)
			System.out.printf("%3d", i);
		System.out.println("\n---+---------------------------");

		for (int i = 1; i <= 9; i++) {
			System.out.printf("%2d |", i);
			for (int j = 1; j <= 9; j++)
				System.out.printf("%3d", i + j);
			System.out.println();
		}
	}
}
````



#### Q14 입력한 수를 한 변으로 하는 정사각형을 *기호로 출력하는 프로그램을 작성하세요.

```java
public class ex01_14 {
	public static void main(String[] args) {
		System.out.println("사각형을 출력합니다.");
		Scanner stdIn = new Scanner(System.in);
		int n = stdIn.nextInt();
		System.out.println("단수 : " + n);
		
		for(int i = 1; i < n; i ++) {
			System.out.println();
			System.out.print("*");
			for(int j = 1; j < n; j++) {
				System.out.print("*");
			}
		}
	}
}
```



#### Q15 직각 이등변 삼각형을 출력하는 부분을 아래와 같은 형식의 메서드로 작성하세요. 또 왼쪽 위, 오른쪽 위, 오른쪽 아래가 직각인 이등변 삼각형을 출력하는 메서드를 작성하세요.

```java
public class ex01_15 {
	public static void main(String[] args) {
		triangleRB(5);
	}

  //왼쪽 아래가 직각인 이등변 삼각형
	static void triangle(int n) {
		for (int i = 1; i < n; i++) {
			for (int j = 1; j <= i; j++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
  
  //왼쪽 위가 직각인 이등변 삼각형
	static void triangleLU(int n) {
		for (int i = 1; i < n; i++) {
			for(int j = 1; j <= n - i; j ++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}

   //오른쪽 위가 직각인 이등변 삼각형
	static void trianglRU(int n) {
		for (int i = 1; i <= n; i++) {
			for(int j = 1; j <= i -1; j ++) {
				System.out.print(" ");
			}
			
			for(int j = 1; j <= n - i + 1; j ++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
  
	 //오른쪽 아래가 직각인 이등변 삼각형
	static void triangleRB(int n) {
		for (int i = 1; i <= n; i++) {
			for(int j = 1; j <= n - i; j ++) {
				System.out.print(" ");
			}
			
			for(int j = 1; j <= i; j ++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```



#### Q15 n단의 피라미를 출력하는 메서드를 작성하세요

```java
public class ex01_16 {
	public static void main(String[] args) {
		spira(3);
	}

	static void spira(int n) {
		for (int i = 1; i <= n; i++) {
			for (int j = 1; j <= n - i; j++) {
				System.out.print(" ");
			}

			for (int j = 1; j <= i; j++) {
				System.out.print("*");
			}

			for (int j = 1; j < i; j++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```

오른쪽아래가 직각인 이등변 삼각형 + 왼쪽 아래가 직각인 이등변 삼각형



#### Q16 오른쪽과 같이 아래를 향한 n단의 숫자 피라미드를 출력하는 매서드를 작성하세요.

```java
public class ex01_17 {
	public static void main(String[] args) {
		npira(4);
	}
	
	static void npira(int n) {
		for (int i = 1; i <= n; i++) {
			for (int j = 1; j <= n - i; j++) {
				System.out.print(" ");
			}

			for (int j = 1; j <= i; j++) {
				System.out.print(i %10);
			}

			for (int j = 1; j < i; j++) {
				System.out.print(i %10);
			}
			System.out.println();
		}
	}
}
```

