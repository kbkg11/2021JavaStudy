# 인터페이스

### 인터페이스란?

- 인터페이스는 상수와 추상메소드만을 가질 수 있음.
- private를 사용할 수 없음.
- 만들어야 할 내용을 안내하는 작업명세서와 같음.

```java
public interface Interface1 {
    final String inf1= "첫 번째 인터페이스";

	public void Interface1();
}

public interface Interface2 {
	final String inf2 = "두 번째 인터페이스";

	public void Interface2();
}
```

```java
public class InterfaceClass implements Interface1, Interface2 {
	final String infMain = "메인 인터페이스입니다.";

	@Override
	public void Interface2() {
		System.out.println(inf2);

	}

	@Override
	public void Interface1() {
		System.out.println(inf1);

	}

	public void InterfaceClass() {
		System.out.println(infMain);
	}

}
```

```java
public class Main {

	public static void main(String[] args) {

		InterfaceClass interfaceClass = new InterfaceClass();
		interfaceClass.InterfaceClass();
		interfaceClass.Interface1();
		interfaceClass.Interface2();

	}

}
```

- 접근을 제한하는 용도로도 쓰인다.

```java
public class Main {

	public static void main(String[] args) {

		InterfaceClass interfaceClass = new InterfaceClass();
		Interface1 interface1 = new InterfaceClass();
		Interface2 interface2 = new InterfaceClass();

		interfaceClass.InterfaceClass();

		interface1.InterfaceClass();
		interface2.InterfaceClass();
		//같은 InterfaceClass 생성자로 만들어졌지만,        InterfaceClass안에 있는 메소드를 사용하지 못한다.
	}

}
```

- 다형성(여러가지 형태를 가질 수 있음) 덕분에 배열로도 만들어 사용할 수 다.

```java
IFunctiion interface1 = new IFunctiion();
IFunctiion interface2 = new IFunctiion();
IFunctiion interface3 = new IFunctiion();
IFunctiion[] iFuntions = {interface1, interface2, interface3}
```

<br>

### 인터페이스를 활용하여 간단한 검색기능 만들기

<img src ="../img/implements.jpg" width="500px" >

```java
public interface Stuff {
//인터페이스들을 하나로 묶어주기 위해 생성
}

public interface Cosmetics extends Stuff{
	final String COSMETICE = "화장품";
	public void Cosmetics();
}
public interface Food extends Stuff{
	final String FOOD = "음식";
	public void Food();
}
public interface Garments extends Stuff{
	final String GARMENTS = "의류";
	public void Garments();
}
public interface HomeAppliance extends Stuff{
	final String HOMEAPPLIANCE = "가전제품";
	public void HomeAppliance();
}
```

```java
public class Coupang implements Food, Garments, HomeAppliance {

	public Coupang() {
		System.out.println("쿠팡에서 파는 물건");
		Garments();
		Food();
		HomeAppliance();
	}

	@Override
	public void HomeAppliance() {
		System.out.println(HOMEAPPLIANCE);
		System.out.println("여름 가전제품");
		System.out.println("겨울 가전제품");
		System.out.println("청소 가전제품\n");
	}

	@Override
	public void Garments() {
		System.out.println(GARMENTS);
		System.out.println("바지");
		System.out.println("잠바");
		System.out.println("속옷\n");

	}

	@Override
	public void Food() {
		System.out.println(FOOD);
		System.out.println("냉동식품");
		System.out.println("음료수");
		System.out.println("즉석식품\n");
	}

}
```

```java

public class Gmarket implements Food, Garments, Cosmetics {

	public Gmarket() {
	 	 System.out.println("g마켓에서 파는 물건");
		 Garments();
		 Food();
		 Cosmetics();
	}

	@Override
	public void Garments() {
		System.out.println(GARMENTS);
		System.out.println("바지");
		System.out.println("잠바");
		System.out.println("속옷\n");
	}

	@Override
	public void Food() {
		System.out.println(FOOD);
		System.out.println("냉동식품");
		System.out.println("음료수");
		System.out.println("즉석식품\n");
	}

	@Override
	public void Cosmetics() {
		System.out.println(COSMETICE);
		System.out.println("로션");
		System.out.println("스킨");
		System.out.println("썬크림\n");
	}
}
```

```java
public class Marketkurly implements Food, Cosmetics, HomeAppliance {

	public Marketkurly() {
	 	 System.out.println("마켓컬리에서 파는 물건");
	 	 Cosmetics();
		 Food();
		 HomeAppliance();
	}
	public void HomeAppliance() {
		System.out.println(HOMEAPPLIANCE);
		System.out.println("여름 가전제품");
		System.out.println("겨울 가전제품");
		System.out.println("청소 가전제품\n");
        }

	@Override
	public void Food() {
		System.out.println(FOOD);
		System.out.println("냉동식품");
		System.out.println("음료수");
		System.out.println("즉석식품\n");
	}

	@Override
	public void Cosmetics() {
		System.out.println(COSMETICE);
		System.out.println("로션");
		System.out.println("스킨");
		System.out.println("썬크림\n");
	}
}
```

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		System.out.println("쇼핑몰이름을 입력해주세요(쿠팡, 마켓컬리, G마켓)");
		System.out.print("검색: ");
		String market = sc.nextLine();

		if (market.equals("쿠팡")) {
			Stuff coupang = new Coupang();
		} else if (market.equals("G마켓")) {
			Stuff gnarket = new Gmarket();
		} else if (market.equals("마켓컬리")) {
			Stuff marketkurly = new Marketkurly();
		} else {
			System.out.println("잘못입력하셨습니다.");
		}

	}

}

실행결과
---------------------------------------------
쇼핑몰이름을 입력해주세요(쿠팡, 마켓컬리, G마켓)
검색: 쿠팡
쿠팡에서 파는 물건
의류
바지
잠바
속옷

음식
냉동식품
음료수
즉석식품

가전제품
여름 가전제품
겨울 가전제품
청소 가전제품
```

## 인터페이스와 추상클래스의 차이점

### 공통점

- 추상메소드를 가지고 있음.
- 데이터타입이 목적임. - 객체생성이 목적이 아닌 데이터 타입을 정의하는 것이 목적
- 객체 생성은 'anonymose'를 이용해야함

### 차이점

- 추상메소드는 상속을 통한 사용이고 인터페이스는 구현을 통한 사용이다.
- 추상클래스는 일반클래스와 동일하게 변수, 메소드의 모든 기능 사용가능하며 단일 상속만 지원한다.

<br>

<br>

# 패턴을 통한 객체지향 언어의 이해

## 패턴(디자인패턴)이란?

- 객체지형 언어의 장점들을 모아 가장 효율적으로 개발을 할 수 있게 만들어 놓은 틀.

<br>

## 싱글턴 패턴

**싱글턴 패턴이란 생성자가 여러 처례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다.**

### 사용하는 경우

- 공통된 객체를 여러개 생성해서 사용하는 상황에서 많이 사용함.
- 인스턴스가 남용되는 것을 방지하기 위해서.

<br>

### 싱글턴패턴을 이용해서 비밀번호 관리하기

```java
public class Singleton {
	private static Singleton printer = new Singleton();
	// printer 변수는 Singleton클래스 안에서만 사용가능.
	String pw = "";

	private Singleton() {
	}
	// Singleton 생성자는 해당클레스에서만 사용할 수 있음.

	public static Singleton getInstance() {
		// 이 메소드는 static이기 때문에 데이터영역에 있음
		// 반환형이 Singleton이기 때문에 본인을 반환한다.
		if (printer == null) {
			printer = new Singleton();
			// printer에 new Singleton() 할당
		}
		return printer;
	}
	// 이 과정은 힙영역이 아닌 데이터영역에서 이루어 지기때문에 여러곳에서 접근하여도 데이터영역에 하나의 메소드만이 존재한다.

}
```

```java
public class SetPw {
	public SetPw() {
		Singleton singleton = Singleton.getInstance();
		System.out.println("비밀번호 조회결과: " + singleton.pw);
	}

}

```

```java
import java.util.Scanner;

public class GatPw {
	public GatPw() {
		Singleton singleton = Singleton.getInstance();
		Scanner sc = new Scanner(System.in);
		System.out.print("비밀번호 재입력: ");
		singleton.pw = sc.nextLine();
		System.out.print("비밀번호가 재입력 되었습니다.");

	}
}
```

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		Singleton singleton = Singleton.getInstance();
		String check;
		System.out.print("비밀번호를 입력하세요: ");
		singleton.pw = sc.nextLine();
		System.out.println("비밀번호입력이 완료되었습니다.");
		do {

			System.out.println("\n비밀번호 관리하기(조회, 수정, 종료)");
			System.out.print("입력: ");
			check = sc.next();
			System.out.println();
			if (check.equals("조회")) {
				SetPw setpw = new SetPw();
			} else if (check.equals("수정")) {
				GatPw gatpw = new GatPw();
				System.out.println();
			} else if (check.equals("종료")) {
				break;
			} else {
				System.out.println("다시입력해주세요(조회, 수정, 종료)");
			}

		} while (true);
		System.out.println("프로그램이 종료되었습니다.");
	}

}


실행결과
---------------------------------
비밀번호를 입력하세요: happy1111
비밀번호입력이 완료되었습니다.

비밀번호 관리하기(조회, 수정, 종료)
입력: 조회

비밀번호 조회결과: happy1111

비밀번호 관리하기(조회, 수정, 종료)
입력: 수정

비밀번호 재입력: happy2222
비밀번호가 재입력 되었습니다.

비밀번호 관리하기(조회, 수정, 종료)
입력: 조회

비밀번호 조회결과: happy2222

비밀번호 관리하기(조회, 수정, 종료)
입력: 종료

프로그램이 종료되었습니다.
```
