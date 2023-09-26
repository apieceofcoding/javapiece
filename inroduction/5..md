# 5. 처음으로 자바 프로그램 짜보기



### 5.1 "Hello, World!" 프로그램 작성

#### 프로그램 코드 작성

```java
public class Example {
    public static void main(String[] args) {
        // "Hello, World!"를 출력하는 코드
        System.out.println("Hello, World!");
    }
}
```

* `Example` 클래스: 자바 프로그램은 클래스로 시작합니다.
* `main` 메서드: 모든 자바 애플리케이션은 `main` 메서드로부터 시작합니다. `public static void main(String[] args)`는 프로그램의 진입점입니다.
* `System.out.println()`: 화면에 텍스트를 출력하는 메서드입니다. "Hello, World!"를 출력합니다.
* `//`: 두 슬래시 (`//`)로 시작하는 부분은 주석(comment)으로 처리되며, 프로그램 실행에 영향을 주지 않습니다. 주석은 코드를 설명하고 문서화하는 데 사용됩니다.

### 5.2 컴파일과 실행

#### 컴파일

1. 터미널 또는 명령 프롬프트에서 프로그램이 저장된 디렉토리로 이동합니다.
2.  다음 명령을 사용하여 프로그램을 컴파일합니다.

    ```
    javac Example.java
    ```

    * `javac`: 자바 컴파일러 명령어입니다.
    * `Example.java`: 컴파일할 자바 소스 코드 파일입니다.
3. 컴파일이 성공하면 현재 디렉토리에 `Example.class` 파일이 생성됩니다.

#### 실행

1.  컴파일된 클래스를 실행하기 위해 다음 명령을 사용합니다.

    ```
    java Example
    ```

    * `java`: 자바 실행기 명령어입니다.
    * `Example`: 실행할 클래스의 이름입니다.
2. 실행 결과로 "Hello, World!"가 출력됩니다.

###
