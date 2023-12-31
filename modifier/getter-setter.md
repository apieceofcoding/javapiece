# 접근자(Getter)와 수정자(Setter)



우리가 현재까지 배웠던 예시에서는 필드에 별도로 접근제어자를 붙이지 않는 default 접근제어자를 사용을 했었습니다.

따라서 동일 패키지 내 다른 클래스에서 `.` 을 통해 바로 필드에 접근하고, 필드를 수정할 수 있었습니다.

```java
public class Counter {
    int count;
}
```

```java
public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
        int count = counter.count; // 접근
        counter.count = 1; // 수정
    }
}
```



하지만, 자바 개발자들 사이에서는 클래스 내부의 변수를 밖에서 사용하지 않도록 하는 관례가 있습니다. 정보 은닉과 캡슐화를 통해 클래스의 내부 구현을 외부로부터 감추고, 안전하게 데이터를 다룰 수 있기 위함입니다.

따라서 prviate 접근제어자로 이 필드에 외부에서 접근, 사용을 막은 후, 외부에서 이 멤버변수에 접근하고 조작이 필요한 경우는 getter와 setter 메서드를 만들어 사용합니다.



## **Getter 메서드**

* Getter는 클래스의 private 멤버 변수의 값을 외부에서 읽을 수 있도록 하는 메서드입니다.
* 메서드의 이름은 "get"으로 시작하고, 그 뒤에 변수명을 CamelCase로 붙입니다.
*   반환 형식은 해당 멤버 변수의 자료형과 일치합니다.

    ```java
    public class Counter {
        private int count;

        // Getter 메서드
        public int getCount() {
            return count;
        }
    }
    ```



## **Setter 메서드**

* Setter는 클래스의 private 멤버 변수의 값을 외부에서 수정할 수 있도록 하는 메서드입니다.
* 메서드의 이름은 "set"으로 시작하고, 그 뒤에 변수명을 CamelCase로 붙입니다.
*   일반적으로 파라미터를 받아 해당 변수에 값을 할당합니다.

    ```java
    public class Counter {
        private int count;

        // Setter 메서드
        public void setCount(int count) {
            this.count = count;
        }
    }
    ```



핵심은 위 두 메서드를 항상 구현하는 것이 아닌, 외부에서 필요로 할 경우만 구현하는 것입니다. 접근만 필요하고 수정이 필요하지 않은 경우 Getter 만 사용할 수 있고, 반대의 상황의 경우 Setter 만 구현할 수도 있습니다. 이를 통해 외부에서 내부의 멤버 변수를 함부로 사용하는 일을 막을 수 있습니다.&#x20;



