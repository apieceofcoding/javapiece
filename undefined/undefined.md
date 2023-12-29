# 접근제어자

\
자바의 중요한 주제 중 하나인 "접근 제어자"에 대해 자세히 알아보겠습니다.

자바의 접근 제어자는 **클래스, 메서드, 변수** 등의 접근 범위를 제어하는 데 사용됩니다. \
접근제어자는 캡슐화와 관련이 있으며, 이는 객체 지향 프로그래밍에서 중요한 개념 중 하나입니다. \
또한 접근제어자 코드의 가시성과 유지보수성을 높이는 데에 중요한 역할을 합니다.&#x20;



## **접근 제어자의 종류**



*   **public:** 다른 모든 클래스에서 접근 가능

    ```java
    public class Counter {
        public int count;

        public void display() {
            System.out.println("coutn: " + count);
        }
    }
    ```
*   **private:** 같은 클래스에서만 접근 가능

    ```java
    public class Counter {
        private int count;

        public void setCount(int value) {
            count = value;
        }

        public int getCount() {
            return count;
        }
    }
    ```
*   **protected:** 동일 패키지 및 하위 클래스에서 접근 가능

    ```java
    public class Counter {
        private int count;
        
        protected void display() {
            System.out.println("coutn: " + count);
        }
    }
    ```
*   **default(기본):** 동일 패키지 내에서만 접근 가능

    ```java
    public class Counter {
        private int count;
        
        void display() {
            System.out.println("coutn: " + count);
        }
    }
    ```









