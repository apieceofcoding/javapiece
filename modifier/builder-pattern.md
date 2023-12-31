# 빌더패턴 (Builder Pattern)



앞선 단원에서 정적 팩토리 메소드를 배웠습니다.

하지만, 클래스 내에 멤버변수가 여러 개 일 때를 생각해봅시다. 생성자나 정적팩토리메소드로 받아야 할 파라미터 수가 많아지면서 관리가 힘들어집니다. 만약 타입이 같은 변수가 이웃하여 붙어있으면, 혼동이 생기기도 하고 심지어는 개발자가 이를 구분하지 못해 버그가 만들어질 수 있습니다.

&#x20;이를 더 깔끔하게 정돈하면서 객체를 선언하는 방법은 없을까요?

빌더패턴은 이를 가능하게 합니다.

우리가 배웠던 static 제어자를 통해서 빌드 패턴을 정의해 보겠습니다.



먼저 Car 클래스를 정의해봅시다.

```java
public class Car {
    private String brand;
    private String model;
    private int year;

    // 기본 생성자
    public Car() {
    }

    // 매개변수를 받는 생성자
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }
}
```

이렇게 생성자를 사용하면 객체를 생성할 때 필요한 정보를 인스턴스 변수에 설정할 수 있습니다. 그러나 생성자의 매개변수가 많아지면 인자의 순서를 혼동할 수 있고, 특정 매개변수를 생략하기 어렵습니다.





## **빌더 패턴 (Builder Pattern)**

빌더 패턴은 객체를 생성하는 복잡한 과정을 추상화하고, 사용자가 명확하게 이해할 수 있는 방식으로 객체를 구축하는 패턴입니다.

```java
public class Car {
    private String brand;
    private String model;
    private int year;

    public Car() {
    }

    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    public static CarBuilder builder() {
        return new CarBuilder();
    }

    public static class CarBuilder {
        private String brand;
        private String model;
        private int year;

        CarBuilder() {
        }

        public CarBuilder brand(String brand) {
            this.brand = brand;
            return this;
        }

        public CarBuilder model(String model) {
            this.model = model;
            return this;
        }

        public CarBuilder year(int year) {
            this.year = year;
            return this;
        }

        public Car build() {
            return new Car(this.brand, this.model, this.year);
        }

        public String toString() {
            return "Car.CarBuilder(brand=" + this.brand + ", model=" + this.model + ", year=" + this.year + ")";
        }
    }
}
```

빌더 클래스(`CarBuilder`)는 필요한 매개변수를 하나씩 설정할 수 있는 메서드를 제공합니다. 각 메서드는 빌더 자체를 반환하므로 <mark style="background-color:yellow;">메서드 체이닝</mark>을 통해 여러 값을 설정할 수 있습니다. 마지막으로 `build` 메서드를 호출하여 실제 객체(`Car`)를 생성합니다.



## **빌더 패턴 사용 예시**

```java
public class Main {
    public static void main(String[] args) {
        // 빌더 패턴을 사용한 객체 생성
        Car car1 = Car.builder()
            .brand("Toyota")
            .model("Camry")
            .year(2022)
            .build();
    }
}
```

빌더 패턴으로 위와 같이 조금 더 깔끔한 형태로 객체를 생성할 수 있습니다.





