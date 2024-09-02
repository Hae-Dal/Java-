# JVM

### - Java Virtual Machine의 약자로 `자바 가상 머신` 이라는 뜻

### - 여러가지 기기에 Java 프로그램을 실행시킬 수 있는 가상의 기기를 만들어주는 것을 의미

![](/img/JVM_example.png)

### 기본 개념

```
가상 머신 : 가상의 기기를 만들어주는 것'
바이트 코드 : 운영체제가 읽을 수 있는 코드
Java 컴파일러 : java &rarr; class
인터프리터 : 운영체제가 읽은 바이트 코드 &rarr; 기계어
JIT 컴파일러 : 인터프리터 효율 &uarr;
메모리 영역 : Java 데이터 저장하는 영역(운영체제로부터 JVM이 할당받은 영역)
클래스 로더 : Java.class 바이트 코드를 메모리 영역에 저장
가비지 컬렉터 : Java 쓰레기 청소기(메모리 영역에서 안쓰는 데이터를 주기적으로 처리)
JRE(Java Runtime Environment) : 자바 실행 환경
 - Java프로그램을 실행`만` 시킬 수 있음
 - .class 파일만 실행 가능
JDK(Java Development Kit) : 자바 개발 키트
 - JRE의 기능을 포함함
 - .java파일을 .class파일로 변환하는 Java 컴파일러(javac) 기능이 있음
 - 코드 디버깅(jdb) 기능이 있음
```

### JVM에서 프로그램이 동작하는 흐름

![](/img/JVM_program_work_flow.png)

# Java

### JVM은 제일 먼저 클래스의 main 메서드를 실행시킨다.

### 1. 변하는 것(변수), 변하지 않는 것(상수)

저장공간의 선언과 값의 저장

-   저장공간의 선언
    ```
    타입 이름;
    ex) Int number;
    ```
    -   자바 프로그램에서 값을 다루기 위해서는 저장공간의 선언이 필요
    -   선언 할 때는 위와같이 타입과 이름을 명시하여 선언
    -   값의 저장
        -   자바 프로그램에서 저장공간에 값을 저장하는 방법
            1. 선언과 동시에 저장 &rarr; 초기화<br/>
               `Int number = 10;`
            2. 선언 이후에 값을 저장 &rarr; 덮어쓰기<br/>
               `number = 10;`

#### 변수 : 변하는 저장공간

-   자바 프로그램에서 저장하는 대부분의 값 = 변수
-   하나의 값을 저장할 수 있는 저장공간을 의미
-   저장되는 값에 따라 여러 모습을 가짐

    ```
    int number = 10; // 1. 변수로 선언 및 초기화
    number = 11; // 2. 변수의 값 변경(덮어쓰기)
    ```

-   기본형 변수 : 숫자, 문자, Boolean...
    -   논리형 변수 : boolean
        -   True/False 값만 저장
    -   문자형 변수 : char
        -   'A', '1' 과 같은 문자 하나만 저장
    -   정수형 변수 : byte, short, int, long
        -   0,1,2,99와 같은 정수형 숫자값을 저장
        -   정수형 변수 표현 범위
            ```
            각 변수 표현 범위를 넘는 수를 넣으면 오버플로우가 발생, 해당 숫자를 출력하면 다른 값이 표현된다.
            ```
    -   실수형 변수 : float, double
        -   0.123, 0.99999와 같은 소수점 실수값 저장
        -   실수형 변수의 표현 범위
            ```
            정수와 동일하게 오버플로우 발생, 출력하면 다른 값 표현
            ```
            -   float (4byte) : `3.4 * -10^38` ~ `3.4 * 10^38` 범위의 숫자 저장 가능 (부동, 고정 소수점)
            -   double (8byte) : `1.7 * -10^308` ~ ` 1.7 * 10^308` 범위의 숫자 저장 가능 ()
-   참조형 변수 : 별도로 저장한 주소 값을 참조해야하는 변수
    -   문자열 변수 : String
        -   "Apple", "텍스트"와 같은 문장을 저장
            ```
            String message = "Hello World"; // 문자열 저장
            ```
    -   그 외 : Object, Array, List...
        -   객체, 배열, 리스트와 같은 단일 저장공간에 담을 수 없는 값을 저장
            ```
            List<int> alphabet = [0,1,2,3]; // 기본형 변수 여러개 저장
            ```
-   래퍼 클래스 변수
    '기본형 변수를 클래스로 한 번 랩핑(감싸는) 변수'
    - 박싱 vs 언박싱
        - 박싱 : 기본타입 &rarr; 래퍼 클래스 변수 
        - 언박싱 : 래퍼 클래스 변수 &rarr; 기본 타입 변수
            ```
            // 박싱
            int number = 21;
            Integer num = new Integer(number);

            // 언박싱
            int n = num.intValue();
            ```
            
#### 상수 : 변하지 않는 저장공간

-   자바 프로그램에서는 변하지 않을 값을 변하지 않는 저장공간에 저장
-   저장되는 값의 형태에 따라 여러 모습을 가짐
    ```
    final int number = 10; // 1. 상수로 선언 (데이터 타입 앞에 final)
    number = 11; // e2. 변수의 값을 바꾸려하면 에러
    ```
