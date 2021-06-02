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

```
