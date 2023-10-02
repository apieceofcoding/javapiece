# 상속 (Inheritance)

상속은 객체 지향 프로그래밍의 중요한 개념 중 하나로, 클래스 간의 관계를 나타내며 코드 재사용과 확장성을 제공합니다. 자바에서 상속을 어떻게 사용하는지 자세히 살펴보겠습니다.

### 상속 (Inheritance)

상속은 기존 클래스(부모 클래스 또는 슈퍼 클래스)의 특성(멤버 변수 및 메서드)을 새로운 클래스(자식 클래스 또는 서브 클래스)가 재사용하는 것을 말합니다. 자식 클래스는 부모 클래스의 모든 멤버를 상속받으며, 추가적인 멤버나 메서드를 정의할 수 있습니다.

#### 예제: `Vehicle` 클래스와 `Car` 클래스

```java
class Vehicle {
    int speed;

    Vehicle(int speed) {
        this.speed = speed;
    }

    void start() {
        System.out.println("운송수단이 출발합니다.");
    }
}
```

```java
class Car extends Vehicle {
    int fuel;

    Car(int speed, int fuel) {
        super(speed);
        this.fuel = fuel;
    }
    
    boolean hasFuel() {
        return fuel > 0;
    }
}
```

위의 예제에서 `Car` 클래스는 `Vehicle` 클래스를 상속받고 있습니다. `Car` 클래스는 `Vehicle` 클래스의 모든 멤버 변수와 메서드를 상속받으며, `fuel` 멤버 변수와 `hasFuel()` 메서드를 추가로 정의했습니다.



### `super` 키워드

`super` 키워드는 부모 클래스의 멤버 변수 또는 메서드를 자식 클래스에서 참조할 때 사용됩니다. `super`를 사용하여 부모 클래스의 생성자를 호출할 수도 있습니다.



### 메서드 오버라이딩 (Method Overriding)

메서드 오버라이딩은 자식 클래스가 부모 클래스의 메서드를 재정의하는 것을 의미합니다. 메서드 시그니처(이름, 매개변수, 반환 값)는 동일해야 합니다.

```java
class Car extends Vehicle {
    int fuel;

    Car(int speed, int fuel) {
        super(speed);
        this.fuel = fuel;
    }
    
    boolean hasFuel() {
        return fuel > 0;
    }

    @Override
    void start() {
        super.start();
        System.out.println("엔진을 가동합니다.");
    }
}
```

위의 코드에서 `@Override` 어노테이션을 사용하여 `start()` 메서드를 오버라이딩하고 부모 클래스의 동작을 확장했습니다.

`super.start()`를 사용하여 부모 클래스의 `start()` 메서드를 호출하고, 자식 클래스에서 추가 동작을 수행합니다.



### 다른 자식 클래스

```java
class Bicycle extends Vehicle {
    boolean hasBell;

    Bicycle(int speed, boolean hasBell) {
        super(speed);
        this.hasBell = hasBell;
    }

    @Override
    void start() {
        super.start();
        System.out.println("자전거가 출발합니다.");
    }

    void alarm() {
        if (hasBell) {
            System.out.println("벨을 울립니다.");
        } else {
            System.out.println("(육성) 지나가겠습니다.");
        }
    }
}
```

운송수단 (Vehicle) 을 정의해 놓았으므로 그 하위의 다른 운송수단도 손쉽게 추가 가능합니다.

부모클래스가 가진 `speed` 필드와 `start()` 메소드를 그대로 물려받을 수 있으며, 위와 같이 `start()` 메소드를 재정의 (override) 할 수 있습니다.





### 다형성 (Polymorphism)

다형성은 상속과 관련하여 부모 클래스 타입의 변수로 자식 클래스의 객체를 참조할 수 있는 개념을 나타냅니다. 이는 객체 지향 프로그래밍의 중요한 특징 중 하나입니다.

```java
Vehicle myCar = new Car(0, 20);
myCar.start(); // "운송수단이 출발합니다."와 "엔진을 가동합니다."가 출력됩니다.
```

위의 코드에서 `myCar` 변수는 `Vehicle` 클래스의 타입이지만, 실제로 `Car` 클래스의 객체를 참조하고 있습니다. 이렇게 다형성을 사용하면 부모 클래스로 일반화된 코드를 작성할 수 있으며, 런타임에 실제 객체의 메서드가 호출됩니다.



또한 자전거 역시 비슷한 방법으로 생성할 수 있습니다.

```java
Vehicle myBicycle = new Bicycle(0, true);
myBicycle.start(); // "운송수단이 출발합니다."와 "자전거가 출발합니다."가 출력됩니다.
```

이렇게 하면 둘은 공통적으로 `Vehicle` 타입을 가지므로 예를 들어 아래 리스트에서 한 번에 관리할 수 있습니다.

```java
List<Vehicle> vehicles = new ArrayList<>();
vehicles.add(myCar);
vehicles.add(myBicycle);

for (Vehicle vehicle: vehicles) {
    vehicle.start();
}

결과 :
운송수단이 출발합니다.
엔진을 가동합니다.
운송수단이 출발합니다.
자전거가 출발합니다.
```





