# final 제어자

Java에서 `final` 키워드는 변수, 메서드, 클래스에 적용될 수 있으며, 기본적으로 '변하는 것을 방지' 하는 특징이 있습니다.&#x20;

## **final 변수:**

* `final` 키워드를 사용하여 선언된 변수는 한 번 할당되면 값을 변경할 수 없습니다.
*   초기화는 선언과 동시에 이루어져야 하며, 나중에 다시 값을 할당할 수 없습니다.

    ```java
    public class Main {
        public static void main(String[] args) {
            final String name = "장갑";
            name = "양말"; // 오류
        }
    }
    ```

## **final 메서드:**

* `final` 키워드를 메서드 앞에 사용하면 해당 메서드는 하위 클래스에서 오버라이딩 될 수 없습니다.
*   메서드의 구현이 최종적이며, 하위 클래스에서 변경할 수 없습니다.

    <pre class="language-java"><code class="lang-java">public class Product {
        String name;
        
        public final void printName() {
            System.out.println("상품명: " + name);
        }
    }

    <strong>public class EventProduct extends Product {
    </strong>
        // 재정의(override) 불가
        public void printCount() { }
    }
    </code></pre>

## **final 클래스**

* 클래스에 `final` 키워드를 사용하면 해당 클래스는 상속될 수 없습니다.
*   다른 클래스에서 이 클래스를 확장하는 것이 불가능합니다.

    ```java
    // final 클래스
    public final class Product {
        String name;
    }

    // 상속 불가
    public class EventProduct extends Product { }
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
public class Constants {
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

### 불변선언과 디버깅

<pre class="language-java"><code class="lang-java"><strong>public class Product {
</strong>    int price;

    public Product(int price) {
        this.price = price;
    }
}
</code></pre>

상품이 있다고 가정해봅시다.



```java
public class Main {
    public static void main(String[] args) {
        Product product = new Product(10000);
        
        // 100줄이상 로직
        product.price = 9000;
        // 100줄이상 로직

        System.out.println(product.price); // 9000원. 분명 10000원인줄 알았는데?
    }
}
```

상품가격이 우리가 모르는 공간에서 9000원으로 바뀌었습니다.&#x20;

문제는 이를 발견하는데 많은 시간이 걸릴 수 있다는 것입니다.

이 코드 로직이 생소한 사람한테는 변경한 부분을 발견하는 것은 쉽지 않습니다.

지금은 한 클래스 안에 있지만, product 객체가 다른 클래스의 파라미터로 들어가서 로직 분산된다면 그 복잡성은 더 커지게 됩니다.



```java
public class Product {
    final int price; // final 추가

    public Product(int price) {
        this.price = price;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        int price = 10000;
        
        // 100줄이상 로직
        int newPrice = 9000;
        // 100줄이상 로직

        Product product = new Product("장갑", newPrice);
        System.out.println(product.price); // 9000
    }
}
```

반면, final 제어자를 붙이면 개발자는 product.price 를 수정할 수 없으므로 위와 같이 구조를 바꾸게 됩니다.

미리 가격(newPrice)을 구하고 상품 생성할 때 구한 가격을 넣어주는 방식입니다.

그러면, 한 번 생성된 product 객체의 내부값은 그 이후로 변경되지 않는 코드가 만들어지고, 디버깅할 때도 newPrice 를 찾아가면 되니 쉽게 가격이 바뀐 원인을 찾아갈 수 있습니다.





하지만, 결국 product 의 price 를 직접 변경할 수 밖에 없는 상황도 존재합니다.

그럴 때는 아래와 같이 메소드를 만들되, 왜 변경이 일어나는 건지 이유를 메소드명에 녹여주시면 좋습니다.

<pre class="language-java"><code class="lang-java"><strong>public class Product {
</strong>    int price;

    public Product(int price) {
        this.price = price;
    }
    
    public void discountPrice(int discountPrice) {
        this.price -= discountPrice;
    }
}
</code></pre>

그러면 가격 변화가 일어났을 때, discountPrice 메소드에서 가격 변동이 일어난 것인지 의심해볼 수 있고, 원인을 더 수월하게 찾을 수 있을 확률이 높게 됩니다.



하지만, 불변성을 유지하는 이유는 디버깅만을 위함도 있지만 그 외 다양한 장점이 있기 때문에 보통 멤버변수에 final 을 붙여 불변객체로 많이 유지합니다. 그 외 장점은 추후 다시 자세히 설명하겠습니다.



