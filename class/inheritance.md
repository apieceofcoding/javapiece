# 상속 (Inheritance)

상속은 객체 지향 프로그래밍의 중요한 개념 중 하나로, 클래스 간의 관계를 나타내며 코드 재사용과 확장성을 제공합니다. 자바에서 상속을 어떻게 사용하는지 자세히 살펴보겠습니다.

### 상속 (Inheritance)

상속은 기존 클래스(부모 클래스 또는 슈퍼 클래스)의 특성(멤버 변수 및 메서드)을 새로운 클래스(자식 클래스 또는 서브 클래스)가 재사용하는 것을 말합니다. 자식 클래스는 부모 클래스의 모든 멤버를 상속받으며, 추가적인 멤버나 메서드를 정의할 수 있습니다.



#### 전기차가 추가되었습니다!

```java
class ElectricCar {
    String name;
    int mileage;
    int speed;
    int batteryAmount;
}

```

전기차 클래스 (`EletricCar`)는 기존 자동차 클래스(`Car`)와 한가지 다른 변수가 추가되었습니다. 바로 배터리양(batteryAmount) 인데요.&#x20;

기존 코드 `Car`를 추상화하여 재사용해볼 수 있지 않을까요?



이를 위해 `Car` 와 `ElectricCar` 의 공통 필드를 가진 클래스 `Vehicle` 을 만들어보겠습니다.



#### 부모클래스 : `Vehicle` (운송수단) 클래스

```java
class Vehicle {
    String name;
    int mileage;
    int speed;

    Vehicle(String name, int mileage, int speed) {
        this.name = name;
        this.mileage = mileage;
        this.speed = speed;
    }

    void start() {
        System.out.println(name + " 운송수단이 출발합니다.");
    }
}
```

위와 같이 `Vehicle` 이라는 부모 클래스를 정의한 후,

아래와 같이 상속을 이용해 `ElectricCar` 라는 자식클래스를 만들어봅시다.



```java
class ElectricCar extends Vehicle {
    int batteryAmount;

    ElectricCar(String name, int mileage, int speed, int batteryAmount) {
        super(name, mileage, speed);
        this.batteryAmount = batteryAmount;
    }

    @Override
    void start() {
        super.start();
        System.out.println("전기차가 출발합니다.");
    }
}
```

이처럼 운송수단 (Vehicle) 을 정의해 놓았으므로 그 하위의 다른 운송수단도 손쉽게 추가 가능합니다.

부모클래스가 가진 `name, mileage, speed` 필드와 `start()` 메소드를 그대로 물려받을 수 있으며, 위와 같이 `start()` 메소드를 재정의 (override) 할 수 있습니다.



### `super` 키워드

`super` 키워드는 부모 클래스의 멤버 변수 또는 메서드를 자식 클래스에서 참조할 때 사용됩니다. `super`를 사용하여 부모 클래스의 생성자를 호출할 수도 있습니다.



### 메서드 오버라이딩 (Method Overriding)

메서드 오버라이딩은 자식 클래스가 부모 클래스의 메서드를 재정의하는 것을 의미합니다. 메서드 시그니처(이름, 매개변수, 반환 값)는 동일해야 합니다.

위의 코드에서 `@Override` 어노테이션을 사용하여 `start()` 메서드를 오버라이딩하고 부모 클래스의 동작을 확장했습니다.

`super.start()`를 사용하여 부모 클래스의 `start()` 메서드를 호출하고, 자식 클래스에서 추가 동작을 수행합니다.





#### Car 클래스도 Vehicle 상속하기

기존 내연기관차인 `Car` 도 새롭게 만든 부모 클래스 `Vehicle` 을 상속하여 재구성해봅시다.

```java
class Car extends Vehicle {
    int fuel;

    ElectricCar(String name, int mileage, int speed, int fuel) {
        super(name, mileage, speed);
        this.fuel = fuel;
    }
    
    @Override
    void start() {
        super.start();
        System.out.println("내연차가 출발합니다.");
    }
}
```

위의 예제에서 `Car` 클래스는 `Vehicle` 클래스를 상속받고 있습니다. `Car` 클래스는 `Vehicle` 클래스의 모든 멤버 변수와 메서드를 상속받으며, `fuel` 멤버 변수와 `hasFuel()` 메서드를 추가로 정의했습니다.







### 다형성 (Polymorphism)

다형성은 상속과 관련하여 부모 클래스 타입의 변수로 자식 클래스의 객체를 참조할 수 있는 개념을 나타냅니다. 이는 객체 지향 프로그래밍의 중요한 특징 중 하나입니다.

```java
Vehicle myCar = new Car("내연차", 100, 0, 20);
myCar.start(); // "운송수단이 출발합니다."와 "내연차가 출발합니다."가 출력됩니다.
```

위의 코드에서 `myCar` 변수는 `Vehicle` 클래스의 타입이지만, 실제로 `Car` 클래스의 객체를 참조하고 있습니다. 이렇게 다형성을 사용하면 부모 클래스로 일반화된 코드를 작성할 수 있으며, 런타임에 실제 객체의 메서드가 호출됩니다.



또한 전기차 역시 비슷한 방법으로 생성할 수 있습니다.

```java
Vehicle myElectricCar = new ElectricCar("전기차", 200, 0, 70);
myBicycle.start(); // "운송수단이 출발합니다."와 "전기차가 출발합니다."가 출력됩니다.
```

이렇게 하면 둘은 공통적으로 `Vehicle` 타입을 가지므로 예를 들어 아래 리스트에서 한 번에 관리할 수 있습니다.

```java
List<Vehicle> vehicles = new ArrayList<>();
vehicles.add(myCar);
vehicles.add(myElectricCar);

for (Vehicle vehicle: vehicles) {
    vehicle.start();
}

결과 :
운송수단이 출발합니다.
내연차가 출발합니다.
운송수단이 출발합니다.
전기차가 출발합니다.
```





> 💡 자바의 모든 클래스는 `Object` 클래스를 상속합니다.
>
> 따라서 **Object 클래스는 최상위 클래스**라고 볼 수 있고, 모든 클래스는 Object 클래스에서 정의된 기본 메소드를 재정의할 수 있습니다.
>
> 대표적인 메소드로 toString(), equals(), hashCode() 가 있습니다.
>
> * toString() : 클래스를 문자열로 표현하는 방법을 정의합니다.&#x20;
>   * Object 클래스에서 기본적으로 `클래스이름@해시코드` 로 표현됩니다.
>   * 재정의(overriding) 할 때는 주로 본인 클래스의 필드값들을 모아 문자열로 만듭니다. 주로 클래스의 필드값을 출력하여 한번에 볼 때 이 메소드를 재정의하여 사용합니다.
> * equals() : 클래스로부터 정의된 객체들이 같은지 참, 거짓으로 반환합니다.
>   * Object 클래스에서 기본적으로 주소가 같으면 클래스도 같다고 정의합니다.
>   * 재정의(overriding) 할 때는 주로 본인 클래스의 필드값이 모두 같으면 같다고 정의합니다.
> * hashcode() : 클래스의 해시코드(int)를 정의합니다.
>   * Object 클래스에서 내부 구현된 방법으로 정의합니다.
>   * 재정의(overriding) 할 때는 주로 본인 클래스의 필드들의 해시코드의 합으로 정의합니다.
>   * equals() 와 보통 같이 쌍으로 구현하는 것을 권장합니다. (그래야 콜렉션에서도 진정한 equals() 를 구현할 수 있기 때문)
>
>
>
> 우선 여기서는 toString() 만 이해하시고, equals(), hashCode() 는 나중에 배울 OOP(객체지향프로그래밍) 맥락에서 더 정확하게 다룰 예정입니다.



