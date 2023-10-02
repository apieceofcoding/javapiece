# 메소드

### 메소드(Method)

메소드는 클래스 내에서 정의된 함수로, 특정 동작 또는 행동을 나타냅니다. 메소드를 클래스 내에 정의하면 해당 클래스의 객체가 해당 동작을 수행할 수 있습니다.

#### **예제 1: `Car` 클래스에 `accelerate()` 메소드 추가**

```java
class Car {
    String brand;
    int year;
    int speed;

    Car(String b, int y) {
        brand = b;
        year = y;
        speed = 0;
    }

    void start() {
        System.out.println("차량이 출발합니다.");
    }

    void accelerate(int increase) {
        speed += increase;
        System.out.println("속도가 " + increase + "km/h 증가하여 " + speed + "km/h 입니다.");
    }
}
```

위의 코드에서 `accelerate(int increase)` 메소드는 속도를 증가시키는 메소드로, `increase` 매개변수에 전달된 값만큼 속도를 증가시킵니다.



### 메소드 오버로딩(Method Overloading)

메소드 오버로딩은 동일한 메소드 이름을 가지고 매개변수의 수, 타입 또는 순서가 다른 여러 버전의 메소드를 정의하는 것입니다. 이를 통해 다양한 매개변수 조합을 처리할 수 있습니다.

#### **예제 2: `Car` 클래스에 메소드 오버로딩**

```java
class Car {
    String brand;
    int year;
    int speed;

    Car(String b, int y) {
        brand = b;
        year = y;
        speed = 0;
    }

    void start() {
        System.out.println("차량이 출발합니다.");
    }

    // accelerate() 메소드 오버로딩 (버전 1)
    void accelerate(int increase) {
        speed += increase;
        System.out.println("속도가 " + increase + "km/h 증가하여 " + speed + "km/h 입니다.");
    }

    // accelerate() 메소드 오버로딩 (버전 2)
    void accelerate() {
        speed += 10;  // 매개변수가 없는 경우 기본적으로 10km/h 증가
        System.out.println("속도가 10km/h 증가하여 " + speed + "km/h 입니다.");
    }
}
```

위의 코드에서 `accelerate()` 메소드를 오버로딩하여, 매개변수가 없는 경우에는 기본적으로 10km/h씩 속도를 증가시키는 버전을 추가했습니다. 이제 `accelerate()` 메소드를 다음과 같이 호출할 수 있습니다.

```java
javaCopy codeCar myCar = new Car("Toyota", 2022);
myCar.accelerate(20);  // 속도가 20km/h 증가하여 20km/h 입니다.
myCar.accelerate();    // 속도가 10km/h 증가하여 30km/h 입니다.
```

이렇게 메소드 오버로딩을 사용하면 다양한 매개변수 조합을 처리할 수 있으며, 메소드 이름을 보다 직관적으로 사용할 수 있습니다.

