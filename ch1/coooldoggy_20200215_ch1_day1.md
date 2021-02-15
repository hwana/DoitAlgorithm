# 알고리즘이란 ?

#### 순차적 구조

여러문장(프로세스)이 순차적으로 실행되는 구조

#### 선택 구조

식의 평가 결과에 따라 프로그램의 실행 흐름을 변경하는 if문 

#### 알고리즘

문제를 해결하기 위한 것으로, 명확하게 정의되고 순서가 있는 유한 개의 규칙으로 이루어진 집합



# 연습문제

#### Q1 네 값의 최댓값을 구하는 max4 메서드를 작성하세요. 

```java
public class ex01_1 {
	public static void main(String[] args) {	
		System.out.println(max4(4,7,9,2));
	}
	
	/**
	 * 네 값의 최댓값을 구하는 max4 메서드를 작성하세요. 
	 * @param a
	 * @param b
	 * @param c
	 * @param d
	 * @return
	 */
	public static int max4(int a, int b, int c, int d) {
		int max = a;
		if(b > max) 
			max = b;
		if(c > max)
			max = c;
		if(d > max)
			max = d;
		return max;
	}
}

```



#### Q2 세 값의 최솟값을 구하는 min3 메서드를 작성하세요.

```java
public class ex01_2 {
	public static void main(String[] args) {
		System.out.println(min3(3,9,8));
	}
	
	/**
	 * 세 값의 최솟값을 구하는 min3 메서드를 작성하세요.
	 * @param a
	 * @param b
	 * @param c
	 * @return
	 */
	public static int min3(int a, int b, int c) {
		int min = a;
		if(min > b)
			min = b;
		if(min > c)
			min = c;
		
		return min;
	}
}
```



#### Q3 네 값의 최솟값을 구하는 min4 메서드를 작성하세요.

```java
public class ex01_3 {
	public static void main(String[] args) {
		System.out.println(min4(4,8,10,1));
	}
	
	/**
	 * 네 값의 최솟값을 구하는 min4 메서드를 작성하세요.
	 * @param a
	 * @param b
	 * @param c
	 * @param d
	 * @return
	 */
	public static int min4(int a, int b, int c, int d) {
		int min = a;
		if(min > b)
			min = b;
		if(min > c)
			min = c;
		if(min > d)
			min = d;
		
		return min;
	}
}
```

