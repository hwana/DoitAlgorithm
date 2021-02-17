# 조건 판단과 분기

## 연산자와 피연산자

##### 단항 연산자 

 피연산자 1개 예) a++

##### 2항 연산자 

 피연산자 2개 예)  a < b

##### 3항 연산자 

피연산자 3개 예) a? b : c 

Java에서 유일한 3항 연산자 



### 반복

##### Q6 실습 1-4에서 while문이 종료될 때 변수 i 값이 n+1이 됨을 확인하세요 (변수 i 값을 출력하도록 프로그램을 수정하세요)

```java
public class ex01_4 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);
		System.out.println("1부터 n까지의 합을 구합니다.");
		System.out.println("n의 값 : ");
		int n = stdIn.nextInt();
		
		int sum = 0;
		int i = 1;
		
		while(i <= n) {
			sum += i;
			i++;
		}
		System.out.println("i 값은 "+ i );
		System.out.println("1부터 " +n +"까지의 합은 "+ sum + "입니다.");
	}
}
```



##### Q7 실습 1-5 프로그램을 참고하여 n이 7이면 '1+2+3+4+5+6+7 = 28'로 출력하는 프로그램을 작성하세요.

```java
public class ex01_7 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);
		
		System.out.println("1부터 n까지의 합을 구합니다.");
		System.out.println("n의 값 :");
		int n = stdIn.nextInt();
		
		int sum = 0;
		
    for(int i =0; i <= n; i++) {
			sum += i;
		}
		
		System.out.println(getPlusString(n, sum));
	}
	
	static String getPlusString(int number, int sum) {
		String returnStr = "";
		String plus = "+";
		String equalStr = "=";
		
    for(int i = 1; i <= number; i ++) {
			if(i == number) {
				returnStr = returnStr + i + equalStr + sum;
			}else if(i == 1){
				returnStr = i + plus;
			}else {
				returnStr = returnStr + i + plus;
			}
		}
		return returnStr;
	}
}
```



#### 가우스의 덧셈

1부터 n까지의 합을 구할때 (1+n)*(n/2)의 방법으로 구할 수 있음 

n이 짝수일때는 성립, n이 홀수일때는 n에서 1을 빼고 계산한 뒤 마지막 숫자를 더해주면 됨



##### Q8 1부터 10까지의 합은 (1+10)*5 와 같은 방법으로 구할 수 있습니다. 가우스의 덧셈이라는 방법을 이용하여 1부터 n까지의 정수 합을 구하는 프로그램을 작성하세요. 

```java
public class ex01_08 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);
		System.out.println("1부터 n까지의 합을 구합니다.");
		System.out.println("n의 값 :");
		int n = stdIn.nextInt();
		
		if(n %2 == 0) {
			System.out.println("n값의 합은 : "+ gaudiPlus(n));
		}else {
			int sum = gaudiPlus(n - 1);
			sum = sum + n;
			System.out.println("n값의 합은 : "+ sum);
		}
	}
	
	static int gaudiPlus(int number) {
		int sum = (number+1)*(number/2);
		return sum;
	}
}
```



##### Q9 정수 a,b를 포함하여 그 사이의 모든 정수의 합을 구하여 반환하는 아래 메서드를 작성하세요.

```java
public class ex01_9 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);
		int a = stdIn.nextInt();
		int b = stdIn.nextInt();
		System.out.println( a +"부터" + b +"까지의 합을 구합니다.");
		System.out.println(sumof(a, b));
	}
	
	static int sumof(int a, int b) {
		int sum = 0;
		int temp = 0;
		if(a > b) {
			temp = b;
			b = a;
			a = temp;
		}
		for(int i = a; i <= b; i++) {
			sum += i;
		}
		
		return sum;
	}
}

```



##### Q10 두변수 a,b에 정수를 입력하고 b-a를 출력하는 프로그램을 작성하세요 .

```java
public class ex01_10 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);
		System.out.print("a의 값：");
		int a = stdIn.nextInt();

		int b=0;
		while (true) {
			System.out.print("b의 값：");
			b = stdIn.nextInt();
			if (b > a)
				break;
			System.out.println("a보다 큰 값을 입력하세요!");
		}

		System.out.println("b - a는 " + (b - a) + "입니다.");
		
	}
}
```



##### Q11 양의 정수를 입력하고 자릿수를 출력하는 프로그램을 작성하세요. 예를들어 135를 입력하면 '그 수는 3자리입니다'라고 출력하고, 1314를 입력하면 '그 수는 4자리 입니다'라고 출력하면 됩니다. 

```java
public class ex01_11 {
	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);

		int n;
		do {
			System.out.print("정수값：");
			n = stdIn.nextInt();
		} while (n <= 0);

		int numberCount = 0; 			
		while (n > 0) {
			n = n/ 10; 			
			numberCount++;
		}

		System.out.println("그 수는 " + numberCount + "자리입니다.");
	}
}
```

