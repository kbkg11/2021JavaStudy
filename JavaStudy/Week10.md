# Collections

## List계열

List는 배열과 비슷하지만, 처음 만들 때 크기를 고정하지 않아도 됩니다.

### ArrayList

```java
	ArrayList<Integer> list = new ArrayList<>();
	//ArrayList 선언

	list.add(10);
	list.add(null);
	//list에 값 추가

	Integer index3 = list.get(0);
    // 값 가져오기

	list.set(0, 20);
	//값 수정하기

	list.size();
	//list 크기 구하기

	list.remove(0);
	//list 0번째 인덱스 값 제거

	list.contains(1);
	//list 0번째 인덱스 값 조회

	list.clear();
	//리스트 날리기

	list = null;
	//리스트 값 날리기

```

### linkedList, vector

```java
LinkedList<String> linkedlist = new LinkedList<String>();
//Arraylist와 거의 비슷, 좀 더 빠름
linkedlist.add(2, "str2");
//2번째칸에 값 추가, 뒤에 자료들 한 칸씩 밀려남

Vector<String> vector = new Vector<String>();
//Arraylist와 거의 비슷, 좀 더 안정적임
```

<br>

## Map계열 컬렉션 클래스

### HashMap

인덱스가 따로 있지 않음. 키값과 데이터만을 이용함

```java
    HashMap<Integer, String> hashMap = new HashMap<Integer, String>();
    hashMap.put(0, "str0");
    hashMap.put(1, "str1");
    //값 넣기
    String str = hashMap.get(1);
    //값 가져오기
    hashMap.remove(1);
    //값 삭제
    hashMap.clear();
```

<br>

HashMap을 이용한 예제 만들기

```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		HashMap<Integer, String> hashMap = new HashMap<Integer, String>();
		boolean exit = false;
		System.out.println("주차관리 프로그램");
		do {
			System.out.println("1 : 자동차 주차하기");
			System.out.println("2 : 자동차 확인하기");
			System.out.println("3 : 모든 자동차 확인하기");
			System.out.println("4 : 주차된 자동차 가져오기");
			System.out.println("5 : 프로그램 종료하기");
			System.out.print("입력: ");
			int sw = sc.nextInt();

			switch (sw) {
			case 1: {
				System.out.println("\n사용하실 자리 번호를 입력하세요 (1~100)");
				System.out.print("번호입력: ");
				int key = sc.nextInt();
				if (key <= 0 || key > 100) {
					System.out.println("번호를 제대로 입력해주세요.\n");
					continue;
				}

				System.out.println("\n주차하실 자동차 번호를 입력하세요");
				System.out.print("입력: ");
				String Value = sc.next();
				hashMap.put(key, Value);
				System.out.println();
				break;
			}
			case 2: {
				System.out.print("\n자리 번호 입력: ");
				int indexKey = sc.nextInt();
				System.out.print("\n주차된 자동차번호: ");
				System.out.println(hashMap.get(indexKey));
				System.out.println();

				break;
			}
			case 3: {
				System.out.println();
				Iterator<Integer> iterator = hashMap.keySet().iterator();
				while (iterator.hasNext()) {
					System.out.print("주차된 자동차번호: ");
					System.out.println(hashMap.get(iterator.next()));
				}
				System.out.println();
				break;
			}
			case 4: {
				System.out.print("\n자리 번호 입력: ");
				int indexKey = sc.nextInt();
				hashMap.remove(indexKey);
				System.out.println();

				break;
			}
			case 5: {
				exit = true;
				break;
			}
			}

		} while (exit == false);

	}
}
실행결과
----------------------------------------

주차관리 프로그램
1 : 자동차 주차하기
2 : 자동차 확인하기
3 : 모든 자동차 확인하기
4 : 주차된 자동차 가져오기
5 : 프로그램 종료하기
입력: 1

사용하실 자리 번호를 입력하세요 (1~100)
번호입력: 23

주차하실 자동차 번호를 입력하세요
입력: 1353육4140

1 : 자동차 주차하기
2 : 자동차 확인하기
3 : 모든 자동차 확인하기
4 : 주차된 자동차 가져오기
5 : 프로그램 종료하기
입력: 1

사용하실 자리 번호를 입력하세요 (1~100)
번호입력: 56

주차하실 자동차 번호를 입력하세요
입력: 49칠73891

1 : 자동차 주차하기
2 : 자동차 확인하기
3 : 모든 자동차 확인하기
4 : 주차된 자동차 가져오기
5 : 프로그램 종료하기
입력: 2

자리 번호 입력: 56

주차된 자동차번호: 49칠73891

1 : 자동차 주차하기
2 : 자동차 확인하기
3 : 모든 자동차 확인하기
4 : 주차된 자동차 가져오기
5 : 프로그램 종료하기
입력: 3

주차된 자동차번호: 1353육4140
주차된 자동차번호: 49칠73891

1 : 자동차 주차하기
2 : 자동차 확인하기
3 : 모든 자동차 확인하기
4 : 주차된 자동차 가져오기
5 : 프로그램 종료하기
입력: 5
```

<br>

### HashSet

데이터 순서는 없지만, 중복된 데이터를 허락하지 않습니다.

```java
	HashSet<String> hashset = new HashSet<String>();
	hashset.add("str0");
	has set.add("str1");
	hashset.add("str2");
	// 값 추가

	System.out.println(hashset.toString());
	// hashset 내용 모두 출력

	hashset.remove("str0");
	//값 삭제
```

<br>

## Iterator 자료구조

Iterator라는 의미는 '반복자'라는 의미로 데이터를 반복적으로 검색하는데 아주 유용함. 모든 자료구조형이 이 메소드를 지원함.

### Iterator

```java
    hashMap.put(0, "str0");
    hashMap.put(1, "str1");
    h ashMap.put(2, "str2");
    Iterator<Integer> iterator = hashMap.keySet().iterator();
    //hashMap.keySet() - hashMap의 키값만 구한것
    //Iterator를 이용해서 hashMap의 키값의 규칙을 구함

    while (iterator.hasNext()) {
        System.out.println(hashMap.get(iterator.next()));
	}
```
