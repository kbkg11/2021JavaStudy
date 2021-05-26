# 문제2

```java
public class Inbody {
	int number;
	String name;
	int age;
	int weight;
	int height;
	public Inbody(int number, String name, int age, int weight, int height) {
		this.number = number;
		this.name = name;
		this.age = age;
		this.weight = weight;
		this.height = height;
	}
}
```

```java

import java.util.ArrayList;
import java.util.Scanner;

public class Student {

	ArrayList<Inbody> members = new ArrayList<Inbody>();

	public static void main(String[] args) {
		// Main클래스 안에 있는 메소드를 사용하기 위해서 Main클래스를 선언
		Student manager = new Student();
		Scanner sc = new Scanner(System.in);
		int number = 0;
		String name;
		int age;
		int weight;
		int height;
		int input;

		while (true) {
			int SwInput, i;
			System.out.println("-------------\n"
			+ 		 "학생 인바디 정보 관리\n" + "-------------\n"
					+ "숫자를 입력해주세요\n"
					+ "1 : 학생정보 추가하기\n"
					+ "2 : 학생정보 조회하기\n" + "3 : 학생정보 수정하기\n"
					+ "4 : 학생정보 삭제하기\n" + "5 : 프로그램 종료하기");
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
				//학생 인바디 정보등록 (학생번호는 자동으로 증가되어서 입력)

				System.out.println("\n학생 정보 추가가 완료되었습니다\n"
				+ "메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
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
				System.out.println("\n학생번호:" + manager.members.get(i - 1).number + " ");
				System.out.println("이름:" + manager.members.get(i - 1).name + " ");
				System.out.println("나이:" + manager.members.get(i - 1).age + " ");
				System.out.println("몸무게:" + manager.members.get(i - 1).weight + " ");
				System.out.println("키:" + manager.members.get(i - 1).height + " ");
				System.out.println("\n조회가 완료되었습니다\n" + "메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
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
				System.out.print("이름: ");
				name = sc.next();
				System.out.print("나이: ");
				age = sc.nextInt();
				System.out.print("몸무게: ");
				weight = sc.nextInt();
				System.out.print("키: ");
				height = sc.nextInt();
				manager.setInbody(i - 1, number, name, age, weight, height);

				System.out.println("\n학생정보 수정이 완료되었습니다\n"
				+ "메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
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
				manager.removeInbody(i - 1);
				System.out.println("\n학생정보 삭제가 완료되었습니다\n"
				+ "메인화면으로 돌아가기 (1)\n" + "프로그램 종료 (2)\n");
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

	public void setInbody(int i, int number, String name, int age,  int weight, int height) {
		members.set(i, new Inbody(number, name, age, weight, height));
	}

	public void removeInbody(int i) {
		members.remove(i);
	}

}

```

**상속기능을 이용하지 않으면, default값을 사용할 수 없다.**

```java
public class MainClass {
	interface InterfaceTest {
	    default void printHello() {
	    	System.out.println("Hello World2");
	        }
	}



	public class DefaultTest {
	    public void main(String[] args) {
	    	MyClass myClass = new MyClass();
	        myClass.printHello();
	    }
	}
}
```
