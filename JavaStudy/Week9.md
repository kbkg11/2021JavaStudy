# API

## Random 클래스

### Matg.randon

```
double b = Math.random();
```

### Random

```
Random = random = new Random();
randem.nextInt(100);
```

<br>

## Wrapper 클래스

기초데이터를 객체데이터로 변화시킨다.

```
Integer integer= new Integer(234);
int i - integer.intValue();
System.out.print(i);
```

## parse

객체데이타를 기초데이터로 변화시킨다.

```
String str = "123";
int i = Integer.parseInt(str);
System.out.println(i + 10);
```

<br>

## Timer, TimerTask 클래스

Timer 클래스 이용해서 스톱워치 만들기

```

import java.util.Scanner;
import java.util.Timer;

public class TimerTest {

	public static void main(String[] args) throws InterruptedException {

		Timer timer = new Timer(true);
		Scanner sc = new Scanner(System.in);
		int s, second = 0;
		String check;
		System.out.println("초를 입력해주세요");
		s = sc.nextInt();
		second = s * 1000;
		int i, j = 0, j2 = 0;
		for (i = 1; i < s; i++) {
			for (j = 0; j < 10; j++) {
				for (j2 = 0; j2 < 10; j2++) {
					Thread.sleep(10);
					System.out.println(i + "." + j + "" + j2);

				}

			}

		}

		Thread.sleep(10);
		System.out.println(i + "초가 지났습니다.");

	}

}
```

<br>

## StringTokenizer 클래스

문자열을 분할 할 때 사용하는 대표적인 클래스.
띄어쓰기를 기준으로 문자열을 분할 해준다.

```
StringTokenizer tokenzer1 = new StringTokenizer(str1);
StringTokenizer tokenzer2 = new StringTokenizer(str2, "/");


tokenzer1.countTokens()
//분할된 문자열의 개수

tokenzer1.hasMoreTokens()
//다음 문자열이 있다면
```

<br>

# 예외처리

## 예외란?

프로그램에서 문제가 발생될 만한 곳을 예상하여 사전에 '문제가 발생하면 아렇게 해라' 라고 지시사항을 프로그래밍 하는 것.

## 예외처리 문법

```java
try{
// 문제가 발생할 수 있는 로직
}catch(Exception e){
// 문제가 발생했을 때 대처방안
e.getMessage()
} finally {
// 문제가 발생하면 무조건 실행됩니다.
}

private void atA() throws Exception{
// 문제가 발생하면 호출한곳에서 처리하게끔 만듦.
}

```

<br>

존재하지 않는 배열 인덱스값을 입력받으면, 예외처리를 이용해서 해결하기

```java
import java.util.ArrayList;
import java.util.Scanner;

import java.util.ArrayList;
import java.util.Scanner;

public class StudentEx {

	ArrayList<Inbody> members = new ArrayList<Inbody>();

	public static void main(String[] args) {
		// Main클래스 안에 있는 메소드를 사용하기 위해서 Main클래스를 선언
		StudentEx manager = new StudentEx();
		Scanner sc = new Scanner(System.in);
		int number = 0;
		String name;
		int age;
		int weight;
		int height;
		int input;

		while (true) {
			int SwInput, i;
			System.out.println("-------------\n" + "학생 인바디 정보 관리\n" + "-------------\n" + "숫자를 입력해주세요\n"
					+ "1 : 학생정보 추가하기\n" + "2 : 학생정보 조회하기\n" + "3 : 학생정보 수정하기\n" + "4 : 학생정보 삭제하기\n" + "5 : 프로그램 종료하기");
			input = sc.nextInt();
			switch (input) {

			case 1: {
				System.out.println("\n학생정보 추가하기");
				System.out.println("학생정보를 입력해주세요(학생번호는 1번부터 자동으로 생성됨)");

				number = number + 1;
				System.out.print("이름: ");
				name = sc.next();
				System.out.print("나이: ");
				age = sc.nextInt();
				System.out.print("몸무게: ");
				weight = sc.nextInt();
				System.out.print("키: ");
				height = sc.nextInt();
				manager.addInbody(number, name, age, weight, height);
				// 학생 인바디 정보등록 (학생번호는 자동으로 증가되어서 입력)

				System.out.println("\n학생 정보 추가가 완료되었습니다\n" + "메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
				SwInput = sc.nextInt();
				if (SwInput == 1) {
					continue;
				} else {
					break;
				}

			}
			case 2: {
				System.out.println("학생 정보 조회하기");
				System.out.print("조회할 학생 번호 입력: ");
				i = sc.nextInt();
				try {
					System.out.println("\n학생번호:" + manager.members.get(i - 1).number + " ");
					System.out.println("이름:" + manager.members.get(i - 1).name + " ");
					System.out.println("나이:" + manager.members.get(i - 1).age + " ");
					System.out.println("몸무게:" + manager.members.get(i - 1).weight + " ");
					System.out.println("키:" + manager.members.get(i - 1).height + " ");
					System.out.println("\n조회가 완료되었습니다");
				} catch (Exception e) {
					System.out.println("\n존재하지 않는 학생번호입니다.");
				}

				System.out.println("\n메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
				SwInput = sc.nextInt();
				if (SwInput == 1) {
					continue;
				} else {
					break;
				}
			}
			case 3: {
				System.out.println("학생정보 수정하기");
				System.out.print("수정할 학생 번호 입력: ");
				i = sc.nextInt();
				try {
					System.out.println("\n학생번호:" + manager.members.get(i - 1).number + " ");
					System.out.println("이름:" + manager.members.get(i - 1).name + " ");
					System.out.println("나이:" + manager.members.get(i - 1).age + " ");
					System.out.println("몸무게:" + manager.members.get(i - 1).weight + " ");
					System.out.println("키:" + manager.members.get(i - 1).height + " ");
					System.out.print("이름: ");
					name = sc.next();
					System.out.print("나이: ");
					age = sc.nextInt();
					System.out.print("몸무게: ");
					weight = sc.nextInt();
					System.out.print("키: ");
					height = sc.nextInt();
					manager.setInbody(i - 1, number, name, age, weight, height);
					System.out.println("\n학생정보 수정이 완료되었습니다");
				} catch (Exception e) {
					System.out.println("\n존재하지 않는 학생번호입니다.");
				}

				System.out.println("\n메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
				SwInput = sc.nextInt();
				if (SwInput == 1) {
					continue;
				} else {
					break;
				}

			}
			case 4: {
				System.out.println("학생정보 삭제하기");
				System.out.print("삭제할 학생의 학생번호입력: ");
				i = sc.nextInt();
				try {
					manager.removeInbody(i - 1);
					System.out.println("\n학생정보 삭제가 완료되었습니다");
				} catch (Exception e) {
					System.out.println("존재하지 않는 학생번호입니다.");
				}

				System.out.println("\n메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
				SwInput = sc.nextInt();
				if (SwInput == 1) {
					continue;
				} else {
					break;
				}
			}
			default:
				break;
			}

			System.out.println("프로그램이 종료되었습니다.");
			break;
		}

	}

	public void addInbody(int number, String name, int age, int weight, int height) {
		members.add(new Inbody(number, name, age, weight, height));
	}

	public void setInbody(int i, int number, String name, int age, int weight, int height) {
		members.set(i, new Inbody(number, name, age, weight, height));
	}

	public void removeInbody(int i) {
		members.remove(i);
	}

}

실행결과
------------------------
-------------
학생 인바디 정보 관리
-------------
숫자를 입력해주세요
1 : 학생정보 추가하기
2 : 학생정보 조회하기
3 : 학생정보 수정하기
4 : 학생정보 삭제하기
5 : 프로그램 종료하기
2
학생 정보 조회하기
조회할 학생 번호 입력: 1

존재하지 않는 학생번호입니다.

메인화면으로 돌아가기 (1)
프로그램 종료 (2)
```

예외 떠넘기기(throws) 이용하기

```java
public class Plus {

	public void Plus(int a, int b) {
		System.out.println(a + b);

	}
}
```

```java
public class Multiply {

	public void Multiply(int a, int b) {
		// TODO Auto-generated method stub
		System.out.println(a * b);
	}

}
```

```java
public class Division {

	public void Division(int a, int b) throws Exception{
		System.out.println(a / b);
	}
}
```

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		int a, b;
		Scanner sc = new Scanner(System.in);
		System.out.println("숫자 두개를 입력해주세요");
		System.out.print("첫 번쨰 숫자: ");
		a = sc.nextInt();
		System.out.print("두 번쨰 숫자: ");
		b = sc.nextInt();

		System.out.print("더하기: ");
		Plus plus = new Plus();
		plus.Plus(a, b);

		System.out.print("곱하기: ");
		Multiply multiply = new Multiply();
		multiply.Multiply(a, b);

		try {
			System.out.print("나누기: ");
			Division division = new Division();
			division.Division(a, b);
		} catch (Exception e) {
			System.out.println("0으로 나눌 수는 없네요");

		}

	}

}

실행결과
------------------------
숫자 두개를 입력해주세요
첫 번쨰 숫자: 10
두 번쨰 숫자: 2
더하기: 12
곱하기: 20
나누기: 5

------------------------
숫자 두개를 입력해주세요
첫 번쨰 숫자: 10
두 번쨰 숫자: 0
더하기: 10
곱하기: 0
나누기: 0으로 나눌 수는 없네요

```

<br>

## 꼭 알아야할 예외들

ArrayIndexOutOfBoundsException - 존재하지 않는 배열 인덱스값 <br>
NullPointException - 존재하지 않는 객체를 가리킬 때 발생<br>
NumberFormatException - 문자를 숫자로 처리할때 발생(숫자로 변경 할 수 없는 문자열을 parse로 변경하려고함) <br>
ClassNotfoundException - 드라이브 이름을 찾지 못했을 떄 <br>
SQLException - db url, id, pw가 올바르지 않을 때
