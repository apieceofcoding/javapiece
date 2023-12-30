# 내부 클래스와 static 내부 클래스



## 내부 클래스

내부 클래스(Inner class)란 클래스 내부에 선언된 클래스를 의미하며, 중첩 클래스(Nested Class)라고도 불립니다.

&#x20;`static` 키워드를 사용하면 정적 중첩 클래스가 됩니다.

```java
public class OuterClass {
    private int outerVariable = 10;

    public class InnerClass {
        private int innerVariable = 20;

        public void display() {
            System.out.println("Outer Variable: " + outerVariable);
            System.out.println("Inner Variable: " + innerVariable);
        }
    }
}
```

OuterClass 안에 선언된 InnerClass (내부클래스) 는 아래와 같이 사용할 수 있습니다.

```java
public class Main {
    public static void main(String[] args) {
        // Outer Class의 인스턴스 생성
        OuterClass outer = new OuterClass();

        // Inner Class의 인스턴스 생성
        OuterClass.InnerClass inner = outer.new InnerClass(20);
        
        inner.display();
    }
}

Outer Variable: 10
Inner Variable: 20
```

내부 클래스에서는 외부클래스의 변수에 접근이 가능합니다. 따라서 display 메소드 안에 outerVariable 을 사용할 수 있습니다.

하지만, InnerClass 의 인스턴스를 만들기 위해서는 반드시 OuterClass 의 인스턴스가 필요한 구조가 됩니다.&#x20;

외부 클래스와 강하게 종속되는 것을 막기 위해서는 static 내부 클래스를 사용할 수 있습니다.





## **Static 내부 클래스**

* 정적  내부 클래스 또는 정적 중첩 클래스라고 합니다.
*   정적 중첩 클래스는 외부 클래스의 인스턴스에 종속되지 않습니다. 따라서 정적 중첩 클래스의 인스턴스를 생성할 때 외부 클래스의 인스턴스를 생성할 필요가 없습니다.

    ```java
    public class OuterClass {
        private static int outerStaticVariable = 5;

        // 정적 중첩 클래스
        public static class StaticNestedClass {
            private int nestedVariable = 10;

            public void display() {
                // 외부 클래스의 정적 변수에 접근
                System.out.println("Outer Static Variable: " + outerStaticVariable);
                // 내부 클래스의 변수에 접근
                System.out.println("Nested Variable: " + nestedVariable);
            }
        }
    }
    ```

```java
public class Main {
    public static void main(String[] args) {
        OuterClass.StaticNestedClass staticNestedObject = new OuterClass.StaticNestedClass();
        staticNestedObject.display();
    }
}

Outer Static Variable: 5
Nested Variable: 10
```



자바는 한 파일에 한 클래스를 선언하는 것이 약속되어 있습니다.

하지만, 해당 클래스 내에서 또 다른 클래스를 내부 클래스로 선언할 수 있습니다. 하지만 이런 구조는 설계를 복잡하게 할 수 있는 단점이 있으므로 trade-off 를 고려하여 설계하는 것이 좋습니다. 내부 클래스가 꼭 필요한 상황인지 고려하여 사용하는 것이 바람직합니다.



