# 패턴을 통한 객체지향 언어의 이해2

## 스트레티지(전략) 패턴

- 어떤 객체를 만들 때 객체가 가지는 다양한 기능들을 추상화 하여 언제든지 적용할 수 있께 기능을 부품화 하는것이다.

<br>

- 스트레티지 패턴 사용하기

1. 개별적인 클래스 만들어서 구현하기.
2. 중복되는 부분은 하나의 클래스을 만들어 상속기능 이용하기. 상속을 이용하다 보니 똑같은 메소드 이름에 기능이 다른경우가 발생하므로 추상메소드를 이용함.
3. 인터페이스를 사용해 각각의 기능을 부품화해서 언제든지 기능을 사용할 수 있게 만들기.

### 스트레티지 패턴을 이용하기

```java
public interface Calendar {
    void Calendar();
}

public interface Kamera {
	void Kamera();
}

public interface music {
    void music();
}
```

```java
public class CalendarYes implements Calendar {

	@Override
	public void Calendar() {
		System.out.println("달력기능이 있습니다.");
	}

}

public class CalendarNo implements Calendar {

	@Override
	public void Calendar() {
		System.out.println("달력기능이 없습니다.");
	}

}

public class KameraYes implements Kamera {

	public void Kamera() {
		System.out.println("카메라기능이 있습니다.");

	}

}

public class KameraNo implements Kamera {

	public void Kamera() {
		System.out.println("카메라기능이 없습니다.");
	}

}
public class Popsong implements music {

	@Override
	public void music() {
		System.out.println("팝송이 들어있습니다.");
	}

}

public class ballad implements music {

	@Override
	public void music() {
		System.out.println("발라드노래가 들어있습니다.");
	}

}

public class MusicNo implements music {

	@Override
	public void music() {
		System.out.println("노래가 없습니다.");
	}

}



```

```java
public class App {
	Kamera Kamera;
	music music;
	Calendar Calendar;

	public void setMusic(music music) {
		this.music = music;
	}

	public void setKamera(Kamera Kamera) {
		this.Kamera = Kamera;
	}

	public void setCalendar(StrategyEx.Calendar Calendar) {
		this.Calendar = Calendar;
	}

	public void getMusic() {
		this.music.music();
	}

	public void getKamera() {
		this.Kamera.Kamera();
	}

	public void getCalendar() {
		this.Calendar.Calendar();
	}
}
```

```java
package StrategyEx;

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		int i = 1;
		String check = "";
		String sw;
		String Icon = "";
		App app = new App();
		Scanner sc = new Scanner(System.in);
		app.setKamera(new KameraNo());
		app.setMusic(new MusicNo());
		app.setCalendar(new CalendarNo());
		do {
			System.out.println("어플을 2개 설치해주세요");
			System.out.println("카메라  노래  달력");
			System.out.println(Icon);
			System.out.print("입력: ");
			sw = sc.next();
			if (sw.equals(check)) {
				System.out.println("\n이미 설치되었습니다.");
				continue;
			}
			if (sw.equals("카메라")) {
				app.setKamera(new KameraYes());
				String kameraIcon = "📷";
				Icon = Icon.concat(kameraIcon);
			} else if (sw.equals("노래")) {
				String MusicIcon = "🎵";
				Icon = Icon.concat(MusicIcon);
				System.out.println("팝송 발라드");
				System.out.print("입력: ");
				sw = sc.next();
				if (sw.equals("팝송")) {
					app.setMusic(new Popsong());
					sw = "노래";

				} else if (sw.equals("발라드")) {
					app.setMusic(new ballad());
					sw = "노래";
				}
			} else if (sw.equals("달력")) {
				app.setCalendar(new CalendarYes());
				String CalendarIcon = "📆";
				Icon = Icon.concat(CalendarIcon);
			} else {
				System.out.println("다시 입력해주세요");
				continue;
			}

			System.out.println();
			check = sw;
			++i;

		} while (i <= 2);
		System.out.println("이 핸드폰에는 ..");
		System.out.println(Icon);
		app.getKamera();
		app.getMusic();
		app.getCalendar();

	}
}

실행결과
-----------------------------
어플을 2개 설치해주세요
카메라  노래  달력

입력: 카메라

어플을 2개 설치해주세요
카메라  노래  달력
📷
입력: 달력

이 핸드폰에는 ..
📷📆
카메라기능이 있습니다.
노래가 없습니다.
달력기능이 있습니다.
```

# 필수 API

## string

### string의 주요 기능들

```
concat : 문자열 연결
substring : 문자열 자르기
lenght : 문자열 길이
toUpperCase : 대문자로 바꾸기
toLowerCase : 소문자로 바꾸기
charAt : 특정위치의 글자 찾기
indexOf : 특정문자열의 위치
equals : 문자열 비교
trim : 문자열 공백제거
replace : 특정문자 변경
replaceAll : 특정문자열 변경
```

```java
String a = "abc";
		String b = "DEF";
		String c = "  ghi  ";

	1	System.out.println(a.concat(b));
	2	System.out.println(a.substring(2));
		//자르고 싶은 문자개수
	3	System.out.println(a.length());
	4	System.out.println(a.toUpperCase());
	5	System.out.println(b.toLowerCase());
	6	System.out.println(a.charAt(2));
		//입력한 인덱스에 해당하는 문자 찾기
	7	System.out.println(+a.indexOf("c"));
		//특정문자열 위치 찾기 (인덱스로 반환)
	8	System.out.println( a.equals(b));
	9	System.out.println(c.trim());
	10	System.out.println(a.replace("a", "b"));
		//문자 "a"를 문자 "b"로 변경
	11	System.out.println(a.replaceAll("abc", "cab"));
		//문자 "abc"를 문자열 "cab"로 변경
실행결과
---------------
1: abcDEF
2: c
3: 3
4: ABC
5: def
6: c
7: 2
8: false
9: ghi
10: bbc
11: cab
```

<br>

## StringBuffer와 StringBuilder

### StringBuilder의 주요 기능들

```
Append : 문자열 추가
insert : 특정위치에 문자열 추가
delete : 문자열 삭제
deleteCharAt : 특정 문자 하나 삭제

```

## 날짜(Calendar)

### Calendar의 주요 기능들

```
Calendar.YEAR
Calendar.MONTH
Calendar.DAY_OF_NONTH
Calendar.HOUR_OF_DAY
Calendar.NINUTE
Calendar.SECOND
```

<br>

## System.currenTimeMillis()

System.currenTimeMillis()는 현재의 시간을 1/1000초 단위로 표시합니다. 거의 속도 테스트 용도로 쓰입니다.

```java
long start = System.currentTimeMillis();
Thread.sleep(5000);
long end = System.currentTimeMillis();
System.out.println("실행시간: " + (end - start) / 1000 + "초");

실행결과
------------------
실행시간: 5초
```
