# final 제어자

Java에서 `final` 키워드는 변수, 메서드, 클래스에 적용될 수 있으며, 기본적으로 '변하는 것을 방지' 하는 특징이 있습니다.&#x20;

## **final 변수:**

* `final` 키워드를 사용하여 선언된 변수는 한 번 할당되면 값을 변경할 수 없습니다.
*   초기화는 선언과 동시에 이루어져야 하며, 나중에 다시 값을 할당할 수 없습니다.

    ```java
    public class Counter {
        final int count = 10;

        public void updateConstant() {
            // 오류! final 변수는 재할당이 불가능합니다.
            count = 20;
        }
    }
    ```

## **final 메서드:**

* `final` 키워드를 메서드 앞에 사용하면 해당 메서드는 하위 클래스에서 오버라이딩 될 수 없습니다.
*   메서드의 구현이 최종적이며, 하위 클래스에서 변경할 수 없습니다.

    ```java
    public class Counter {
        private int count;

        // final 메서드
        public final void printCount() {
            System.out.println("카운트: " + count);
        }
    }

    public class LikesCounter extends Counter {
        // 오류! final 메서드는 오버라이딩이 불가능합니다.
        public void printCount() { }
    }
    ```

## **final 클래스**

* 클래스에 `final` 키워드를 사용하면 해당 클래스는 상속될 수 없습니다.
*   다른 클래스에서 이 클래스를 확장하는 것이 불가능합니다.

    ```java
    // final 클래스
    public final class Counter {
        private int count;
    }

    // 오류! final 클래스는 상속이 불가능합니다.
    public class LikesCounter extends Counter { }
    ```

`final` 키워드는 주로 코드의 안정성과 보안을 강화하기 위해 사용되며, 불변성을 유지하고자 할 때 특히 유용합니다. 변수, 메서드, 클래스에 `final`을 적절히 활용하여 코드의 안정성을 높일 수 있습니다.





## 불변성과 final

내가 설정해놓은 값이 다른 곳에서 몰래 바뀌어버린다면 어떨까요? 문제가 발생하지만, 쉽게 이 버그를 발견하지 못할 확률이 높습니다.

하지만 자바는 기본적으로 가변 (변할 수 있는) 변수로 정의가 되며, 불변성을 필요로 할 경우 final 키워드를 앞에 추가합니다.&#x20;

final 의 장점은 명백합니다. 변수에 초기에 설정해 놓은 값을 다른 곳에서 바꾸지 못하게 함으로써 버그를 줄이고, 문제가 발생해도 디버깅(버그의 원인을 찾는 일)이 수월합니다.

하지만 단점도 있습니다. `final` 키워드가 무분별하게 많이 들어가면서 가독성에 해를 줄 수 있습니다.

이 둘의 trade-off 를 절충하여 적절한 곳에 사용하면 좋은 final 예시를 들어보겠습니다.



### **상수(Constant) 선언**

`final` 키워드를 사용하여 상수를 선언할 수 있습니다. 상수는 한 번 할당되면 값을 변경할 수 없으며, 대문자와 밑줄로 작성된 명명 규칙을 따르는 것이 관례입니다.

```java
public class Constants {\
    // 상수 선언
    public static final int MAX_VALUE = 100;
    public static final String APPLICATION_NAME = "MyApp";

    public static void main(String[] args) {
        // 상수 사용
        System.out.println("Max Value: " + Constants.MAX_VALUE);
        System.out.println("Application Name: " + Constants.APPLICATION_NAME);
    }
}
```

### 데이터 전달 객체 (DTO, Data Transfer Object)

```java
public class Product {
    private final String name;
    private final int price;

    public Product(String name, int price) {
        this.name = name;
        this.price = price;
    }

    // Getter 메서드만 제공하고, Setter를 제공하지 않음
    public String getName() {
        return name;
    }
    
    public int getPrice() {
        return price;
    }
}
```

한 번 초기화된 객체는 외부에서 값을 변경하지 않고, 값의 변경이 필요할 때는 새로운 객체를 만들어 사용하면 불변성을 유지할 수 있습니다.

```java
public class Main {
    public static void main(String[] args) {
        Product product = new Product("장갑", 10000)
        // 할인이 필요한 경우 
        product.price = 9000; // 불가
        
        // 값의 변경이 필요한 경우 새롭게 선언
        Product discountedProduct = new Product("장갑", 9000);
    }
}
```



