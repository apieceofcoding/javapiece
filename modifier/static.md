# static 제어자



```java
public class Application {
    public static void main(String[] args) {
        double pi = 3.141592;
        System.out.println(pi);
    }
}
```

pi (파이) 는 원주율이며, 변하지 않는 상수입니다.&#x20;

그리고 값을 기억하기도 쉽지 않아 매번 정의하여 사용하면 실수가 발생할 수 있습니다.

문제는 이 값이 여러 군데 선언되어 있었는데, 값이 변경될 일이 생겼을 때 관리하기가 어렵습니다.

* 파이는 수학적 값이라 정말 그럴 수 없겠지만, 프로그래밍을 하다보면 이렇게 절대 바뀌지 않으리라 생각했던 것이 꼭 변경되기도 합니다.



## 한 번 정의하고, 공통으로 사용하고 싶다.

위 문제를 어떻게 해결하면 좋을까요?

변수를 한 번 생성하고, 이를 전역적으로 공유해서 사용하면 됩니다.



자바에서는 static 제어자를 통해 변수를 공용공간에 저장하고 사용할 수 있습니다.

자바 실행 시점에 생성되는 이 공용 공간은 런타임 데이터 영역(`Runtime data area`)이라 부르며, static 변수는 런타임 데이터 영역 안의 `method area` 에 저장되게 됩니다.



`main.java` 파일을 컴파일러를 통해 컴파일하면, `main.class` 가 생성됩니다. 그리고 `java` 명령어를 통해 클래스파일을 실행하면, 아래와 같이 JVM 실행 환경이 구성됩니다.

그 중 Runtime Data Areas 에 우리가 선언한 변수가 저장되는데, Method Area 에 static 변수가 저장됩니다.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>자바 컴파일 및 실행 (출처: <a href="https://d2.naver.com/helloworld/1230">https://d2.naver.com/helloworld/1230</a>)</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>런타임 데이터 영역 (출처: <a href="https://d2.naver.com/helloworld/1230">https://d2.naver.com/helloworld/1230</a>)</p></figcaption></figure>

참고로 Runtime Data Areas 에 다양한 저장공간이 있는데, 메소드 호출시에는 메소드 내 필요한 변수들이 Stack(JVM Stack) 영역에 저장되고, new 키워드로 만든 객체들은 Heap 영역에 저장되게 됩니다.

이는 후에 좀 더 자세히 더 배워보겠습니다.





## **Static 변수 (클래스 변수)**

* 클래스의 모든 인스턴스가 공유하는 변수를 정의할 때 사용합니다.

<pre class="language-java"><code class="lang-java"><strong>public class MathUtils {
</strong>    // static 변수
    public static final double PI = 3.14159265358979;
}
</code></pre>

```java
public class Application {
    public static void main(String[] args) {
        double pi = MathUtils.PI;
        System.out.println(pi);
    }
}
```



*   객체가 생성되기 전에 메모리에 할당되며, 모든 인스턴스에서 동일한 값을 유지합니다.

    ```java
    public class Counter {
        // static 변수 (클래스 변수)
        public static int count = 0;

        public Counter() {
            // 생성자가 호출될 때마다 인스턴스 수 증가
            count++;
        }

        public static void main(String[] args) {
            // static 변수 접근
            System.out.println("count: " + Counter.count); // 0

            // 인스턴스 생성
            Counter obj1 = new Counter();
            Counter obj2 = new Counter();

            // static 변수는 모든 인스턴스에서 공유되므로 값이 누적됨
            System.out.println("count: " + Counter.count); // 2
        }
    }
    ```

    따라서 static 변수를 변경해도 되는지 심도있는 고민을 한 후 결정하는 것이 좋으며, 보통 상수로 사용하는 경우는 final 을 붙여 안전하게 변수가 변경되지 않도록 합니다.



## **Static 메서드**

* 클래스의 인스턴스를 만들지 않고 메서드를 정의할 때 사용합니다.
*   주로 유틸리티 메서드나 정적 팩토리 메서드 등을 구현할 때 활용됩니다.

    ```java
    public class MathUtils {
        // static 변수
        public static final double PI = 3.14159265358979;

        // static 메서드
        public static double circumference(int radius) {
            return 2 * PI * radius;
        }
    }
    ```

```java
public class Application {
    public static void main(String[] args) {
        double circumference = MathUtils.circumference(1);
        System.out.println(circumference);
    }
}
```





## **Static 블록 (클래스 초기화 블록)**

* 클래스가 처음으로 로딩될 때 한 번 실행되는 블록으로, 주로 클래스 변수 초기화에 사용됩니다.
*   객체 생성과 관계없이 클래스 로딩 시에 실행됩니다.

    ```java
    public class MathUtils {
        // static 변수
        public static final double PI;

        static {
            System.out.println("PI 초기화");
            PI = 3.14159265358979;
        }
    }
    ```

`static` 제어자는 객체 간에 데이터를 공유하거나 인스턴스를 만들지않고 작업을 수행하는 데 유용합니다. 이를 통해 메모리 사용량을 줄이고 코드 실행 성능을 향상시킬 수 있습니다.

<pre class="language-java"><code class="lang-java">public class Application {
    public static void main(String[] args) {
        double circumference = MathUtils.circumference(1);
        System.out.println(circumference);
    }
}
<strong>
</strong><strong>PI 초기화
</strong>6.28318530717958
</code></pre>





