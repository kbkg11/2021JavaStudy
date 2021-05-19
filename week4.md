### __1. new 연산자의 역할은?__

```
package tset;
public Class MainClass{
        public MainClass(){

        }
MainClass mc = new MainClass();
}
```


<br>

## __2. Array list값을 값을 추가하는 방법과 삭제하는 방법 (빈칸에 값 추가)__
```
ArrayList<Integer> list = new ArrayList<>();
//ArrayList 선언

list.[빈칸](10);
//list에 10이라는 값 추가

list.[빈칸](0);
//list 0번째 인덱스 값 제거	
```

<br>

## __3. Class.pri가 실행되지 않는 이유는?__

```
public class ClassTest{
private void pri() {
  System.out.println("private");
}

```

```
public class Test{
ClassTest Class = new ClassTest();
Class.pri();
}
```

