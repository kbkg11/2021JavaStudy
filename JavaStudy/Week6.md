# 추상클래스

### 추상클래스란?

- 클래스를 추상적으로만 정의해둔다.
- 클래스 앞에 `abstract` 키워드를 넣어사용한다.
- 자식 클래스에서 꼭 재정의해야 하는 부분이 있을 때 사용한다.

<br>

## 추상클래스 이용하기

**추상화클래스 하나로 여러도형 넚이 구하기**

```java
public abstract class Calculation {

	int height;
	int weight;
	int square;
	int triangle;

	public abstract void Figure(int height, int weight);

}
```

```java
public class Square extends Calculation {

	@Override
	public void Figure(int height, int weight) {

		square = height * weight;
		System.out.println("사각형의 넓이는: " + square);

	}

}
```

```java
public class Triangle extends Calculation {

	@Override
	public void Figure(int height, int weight) {
		triangle = (height * weight) / 2;
		System.out.println("삼각형의 넓이는: " + triangle);
	}

}
```

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int height = 0, weight = 0;

		System.out.print("높이: ");
		height = sc.nextInt();
		System.out.print("넓이: ");
		weight = sc.nextInt();

		Square square = new Square();
		square.Figure(height, weight);
		Triangle triangle = new Triangle();
		triangle.Figure(height, weight);

	}

}
```

**기숙사 하루, 한 달 식비 계산하기**

- 조식, 중식, 석식, 간식비를 계산한다.
- 중식은 꼭 먹어야 한다.
- 중식 메뉴와 간식은 정할 수 있다.

```java
public class Expenses {

	public static final int BREAKFAST = 4000;
	public static final int LUNCH_HANSIG = 5000;
	public static final int LUNCH_JUNHSIG = 6000;
	public static final int LUNCH_ILSIG = 5500;
	public static final int DINNER = 5500;
	public static final int SNACK = 1500;
	public static final int DRINK = 1000;

}
```

```java
public abstract class Calculation {
	public int blackfast = 0;
	public int jungsig = 0;
	public int hansig = 0;
	public int ilsig = 0;
	public int dinner = 0;
	public int snack = 0;
	public int drink = 0;

	public void Blackfast(int dlackfast) {
	}

	public abstract void Lunch(int jungsig, int hansig, int ilsig);

	// 중식은 필수 신청이기 떄문에 abstract로 설정
	public void Dinner(int dinner) {
	}

	public void Dessert(int snack, int drink) {
	}

	public abstract int Calculating();
	// 계산은 꼭 해야하므로 떄문에 abstract로 설정
}
```

```java
public class Student1 extends Calculation {

	public void Blackfast(int blackfast) {
		super.blackfast = blackfast;
	}

	public void Lunch(int jungsig, int hansig, int ilsig) {

		super.jungsig = jungsig;
	}

	public void Dinner(int dinner) {
		super.dinner = dinner;
	}

	public void Dessert(int snack, int drink) {
		super.snack = snack;
		super.drink = drink;
	}

	public int Calculating() {
		int sum = blackfast + jungsig + hansig + ilsig + dinner + snack + drink;

		return sum;
	}

}
```

```java
public class Student2 extends Calculation {

	public void Lunch(int jungsig, int hansig, int ilsig) {

		super.ilsig = ilsig;
	}

	public void Dinner(int dinner) {
		super.dinner = dinner;
	}

	public int Calculating() {
		int sum = blackfast + jungsig + hansig + ilsig + dinner + snack + drink;

		return sum;
	}

}
```

```java
public class Main {

	public static char checkBlackfast, checkJungsig,checkHansig,checkIlsig,checkDinner,checkSnack,checkDrink;

	public static void main(String[] args) {
	Student1 studen1 = new Student1();
	Student2 studen2 = new Student2();

	studen1.Blackfast(Expenses.BREAKFAST);
	studen1.Lunch(Expenses.LUNCH_HANSIG, Expenses.LUNCH_JUNHSIG, Expenses.LUNCH_ILSIG);
	studen1.Dinner(Expenses.DINNER);
	studen1.Dessert(Expenses.SNACK, Expenses.DRINK);

	studen2.Blackfast(Expenses.BREAKFAST);
	studen2.Lunch(Expenses.LUNCH_HANSIG, Expenses.LUNCH_JUNHSIG, Expenses.LUNCH_ILSIG);
	studen2.Dinner(Expenses.DINNER);
	studen2.Dessert(Expenses.SNACK, Expenses.DRINK);

	System.out.println("student1의 하루,한 달 급식비: "+ studen1.Calculating() +", " +(studen1.Calculating()*20));
	System.out.println("student2의 하루,한 달 급식비: "+ studen2.Calculating() +", " +(studen2.Calculating()*20));

	}

}

실행결과
----------------------------
student1의 하루,한 달 급식비: 17000, 340000
student2의 하루,한 달 급식비: 11000, 220000

```

<br>

**scanner를 이용해서 만들기**

```java
public class Expenses {

	public static final int BREAKFAS = 4000;
	public static final int LUNCH_HANSIG = 5000;
	public static final int LUNCH_JUNHSIG = 6000;
	public static final int LUNCH_ILSIG = 5500;
	public static final int DINNER = 5500;
	public static final int SNACK = 1500;
	public static final int DRINK = 1000;

}
```

```java
public abstract class Calculation {
	public int blackfast;
	public int jungsig;
	public int hansig;
	public int ilsig;
	public int dinner;
	public int snack;
	public int drink;

	public void Blackfast(int dlackfast) {
	}

	public abstract void Lunch(int jungsig,int hansig,int ilsig);
    //중식은 필수 신청이기 떄문에 추상클래스로 만들기
    public void Dinner(int dinner) {
    }

	public void Dessert(int snack, int drink) {
	}

	public abstract int Calculating();
    //계산은 꼭 해야하므로 떄문에 추상클래스로 만들기
}
```

```java
public class Student2 extends Calculation {

	public void Blackfast(int blackfast) {
		super.blackfast = blackfast;
	}

	public void Lunch(int jungsig, int hansig, int ilsig) {
		super.jungsig = jungsig;
		super.hansig = hansig;
		super.ilsig = ilsig;
	}

	public void Dinner(int dinner) {
		super.dinner = dinner;
	}

	public void Dessert(int snack, int drink) {
		super.snack = snack;
		super.drink = drink;
	}

	public int Calculating() {
		int sum = blackfast + jungsig + hansig + ilsig + dinner + snack + drink;

		return sum;
	}

}
```

```java
import java.util.Scanner;

public class Main {

	public static char checkBlackfast, checkJungsig, checkHansig, checkIlsig, checkDinner, checkSnack, checkDrink;

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Student2 studen2 = new Student2();
		int blackfast = 0, jungsig = 0, hansig = 0, ilsig = 0, dinner = 0, snack = 0, drink = 0;

		System.out.println("급식신청서 (ox로 체크, 점심은 3중1택 필수)");

		System.out.print("조식(4000원): ");
		checkBlackfast = sc.nextLine().charAt(0);
		System.out.print("점심(한식, 5000원): ");
		checkJungsig = sc.nextLine().charAt(0);
		System.out.print("점심(중식, 6000원): ");
		checkHansig = sc.nextLine().charAt(0);
		System.out.print("점심(일식, 6500원): ");
		checkIlsig = sc.nextLine().charAt(0);
		System.out.print("석식(5500원): ");
		checkDinner = sc.nextLine().charAt(0);
		System.out.print("간식(과자, 1500원): ");
		checkSnack = sc.nextLine().charAt(0);
		System.out.print("간식(음료수, 1000원): ");
		checkDrink = sc.nextLine().charAt(0);

		if (checkBlackfast == 'o')
			blackfast = Expenses.BREAKFAS;
		if (Main.checkJungsig == 'o') {
			jungsig += Expenses.LUNCH_JUNHSIG;
		} else if (Main.checkHansig == 'o') {
			hansig += Expenses.LUNCH_HANSIG;
		} else if (Main.checkIlsig == 'o') {
			ilsig += Expenses.LUNCH_ILSIG;
		} else {
			System.out.println("중식을 체크해주세요");
			System.exit(0);
		}
		if (Main.checkIlsig == 'o')
			dinner += Expenses.DINNER;
		if (Main.checkDinner == 'o')
			snack += Expenses.SNACK;
		if (Main.checkSnack == 'o')
			drink += Expenses.DRINK;

		studen2.Blackfast(blackfast);
		studen2.Lunch(jungsig, hansig, ilsig);
		studen2.Dinner(dinner);
		studen2.Dessert(snack, drink);

		System.out.println("\n하루 급식비: " + studen2.Calculating() + "원");
		System.out.println("한 달 급식비: " + (studen2.Calculating() * 20) + "원");

	}

}

실행결과
---------------------------------------------
급식신청서 (ox로 체크, 점심은 3중1택 필수)
조식(4000원): o
점심(한식, 5000원): o
점심(중식, 6000원): x
점심(일식, 6500원): x
석식(5500원): x
간식(과자, 1500원): x
간식(음료수, 1000원): x

하루 급식비: 9000원
한 달 급식비: 180000원

--------------------------------------------
급식신청서 (ox로 체크, 점심은 3중1택 필수)
조식(4000원): o
점심(한식, 5000원): x
점심(중식, 6000원): x
점심(일식, 6500원): x
석식(5500원): o
간식(과자, 1500원): o
간식(음료수, 1000원): o
점심메뉴를 체크해주세요.
```
