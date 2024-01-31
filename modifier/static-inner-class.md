# 내부 클래스와 static 내부 클래스



## 내부 클래스

내부 클래스(Inner class)란 클래스 내부에 선언된 클래스를 의미하며, 중첩 클래스(Nested Class)라고도 불립니다.

&#x20;`static` 키워드를 사용하면 정적 중첩 클래스가 됩니다.

```java
public class Library {
    String name = "판교도서관";

    public class Book {
        String title = "자바한조각";

        public void show() {
            System.out.println("도서관이름: " + name);
            System.out.println("책이름: " + title);
        }
    }
}
```

Library 안에 선언된 Book (내부클래스) 은 아래와 같이 사용할 수 있습니다.

```java
public class Main {
    public static void main(String[] args) {
        // 외부클래스 객체 생성
        Library library = new Library();
        // 내부클래스 객체 생성
        Library.Book book = library.new Book();
        book.show();
    }
}

도서관이름: 자바한조각
책이름: 자바한조각
```

내부 클래스에서는 외부클래스의 변수에 접근이 가능합니다. 따라서 show 메소드 안에 name 변수를 사용할 수 있습니다.

하지만, Book 의 인스턴스를 만들기 위해서는 반드시 Library 의 인스턴스가 필요한 구조가 됩니다.&#x20;

외부 클래스와 강하게 종속되는 것을 막기 위해서는 static 내부 클래스를 사용할 수 있습니다.





## **Static 내부 클래스**

* static 내부 클래스는 외부 클래스의 인스턴스에 종속되지 않습니다. 따라서 static 내부 클래스의 인스턴스를 생성하기 전 외부 클래스의 인스턴스를 생성할 필요가 없습니다.
*   정적 내부 클래스 또는 정적 중첩 클래스라고도 부릅니다.

    ```java
    public class Library {
        static String name = "판교도서관";

        // static 내부클래스
        public static class Book {
            String title = "자바한조각";

            public void show() {
                // 외부클래스의 static 변수 사용
                System.out.println("도서관이름: " + name);
                System.out.println("책이름: " + title);
            }
        }
    }
    ```

```java
public class Main {
    public static void main(String[] args) {
        // static 내부클래스 객체 생성
        Library.Book book = new Library.Book();
        book.show();
    }
}

도서관이름: 판교도서관
책이름: 자바한조각
```



자바는 한 파일에 한 클래스를 선언하는 것이 약속되어 있습니다.

하지만, 해당 클래스 내에서 또 다른 클래스를 내부 클래스로 선언할 수 있습니다. 하지만 이런 구조는 설계를 복잡하게 할 수 있는 단점이 있으므로 trade-off 를 고려하여 설계하는 것이 좋습니다. 내부 클래스가 꼭 필요한 상황인지 고려하여 사용하는 것이 바람직합니다.



