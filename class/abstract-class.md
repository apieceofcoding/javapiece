# 추상클래스 (abstract class)

### 추상클래스



추상클래스는 왜 필요할까요?

* **클래스 설계의 규칙을 만들어줍니다.**
  * 특정 부모클래스를 상속하는 자식클래스에게 반드시 특정 메소드를 재정의 하라고 명시할 수 있습니다.
  * 그렇지 않으면 컴파일 오류가 발생하게 되어 다른 개발자가 규칙을 어기는 것을 방지할 수 있습니다.



#### 추상클래스의 정의

추상 클래스는 하나 이상의 추상 메서드를 포함하고 있는 클래스로, 객체를 직접 생성할 수 없으며 다른 클래스에서 상속하여 구현해야 합니다. 추상 클래스는 `abstract` 키워드를 사용하여 정의하며, 다음과 같은 특징을 가집니다:

* 하나 이상의 추상 메서드를 포함할 수 있습니다.
* 일반 메서드도 가질 수 있습니다.
* 추상 클래스로부터 직접 객체를 생성할 수 없습니다.

#### 추상클래스의 구성

추상 클래스는 다음과 같은 구성 요소를 가질 수 있습니다:

1. **멤버 변수 (Fields):** 일반 멤버 변수를 포함할 수 있습니다.
2. **추상 메서드 (Abstract Methods):** 추상 메서드는 메서드의 시그니처만을 정의하고 구현 내용은 제공하지 않습니다. <mark style="background-color:yellow;">하위 클래스에서는 추상 메서드를</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">**반드시**</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">구체적으로 구현해야 합니다.</mark>
3. **일반 메서드 (Concrete Methods):** 추상 클래스는 추상 메서드 외에도 일반 메서드를 가질 수 있으며, 이 메서드는 구현 내용을 포함합니다.

#### 추상클래스 예제

아래의 예제는 `Vehicle`를 추상 클래스로 정의한 후, `Car`와 `ElectricCar` 클래스에서 이를 상속하고 필요한 메서드를 구현하는 사용 예제입니다.

<pre class="language-java"><code class="lang-java"><strong>abstract class Vehicle {
</strong>    String name;
    int mileage;
    int speed;

    Vehicle(String name, int mileage, int speed) {
        this.name = name;
        this.mileage = mileage;
        this.speed = speed;
    }

    abstract void start(); // 추상 메서드
}
</code></pre>

```java
// Car 클래스는 Vehicle 추상 클래스를 상속하고 추상 메서드 구현
class Car extends Vehicle {
    int fuel;

    Car(String name, int mileage, int speed, int fuel) {
        super(name, mileage, speed, fuel);
        this.fuel = fuel;
    }

    // Vehicle 추상클래스에 있는 추상메소드이므로 반드시 구현
    @Override
    void start() {
        System.out.println(name + " 내연차가 출발합니다.");
    }
    
    // 그 외 메소드 구현 (선택)
    boolean hasFuel() {
        return fuel > 0;
    }
}
```

```java
// ElectricCar 클래스도 Vehicle 추상 클래스를 상속하고 추상 메서드 구현
class ElectricCar extends Vehicle {
    int batteryAmount;

    ElectricCar(String name, int mileage, int speed, int batteryAmount) {
        super(name, mileage, speed);
        this.batteryAmount = batteryAmount;
    }

    // Vehicle 추상클래스에 있는 추상메소드이므로 반드시 구현
    @Override
    void start() {
        System.out.println(name + " 전기차가 출발합니다.");
    }

    // 그 외 메소드 구현 (선택)
    boolean hasBattery() {
        return batteryAmount > 0;
    }
}
```

이 예제에서 `Vehicle`는 추상 클래스로 정의되었고, 하위 클래스인 `Car`와 `ElectricCar`에서 추상 메서드인 `start()`를 구체적으로 구현했습니다. 추상 클래스를 사용하여 공통된 메서드와 추상 메서드를 포함하는 클래스 계층을 구성할 수 있습니다.







추상클래스는 일반 상속에서 부모클래스와 다른 점은 아래와 같습니다.

* `abstract` 키워드를 반드시 클래스 앞에 붙여야 합니다.
* 추상메서드를 제공하고 싶은 경우 그 메서드 앞에 `abstract` 를 붙이면 됩니다.
* 추상클래스는 직접 인스턴스를 만들 수 없습니다. 자식클래스가 추상클래스를 상속받은 후 자식클래스에서는 인스턴스를 만들 수 있습니다. (생성자는 만들 수 있으나, 자식클래스에서 `super` 를 통해서만 사용할 수 있습니다.)

추상클래스는 부모 클래스에 조금 더 명시적인 제약을 두고 싶을 때 유용합니다.

예를 들어 자식 클래스가 부모 클래스를 상속했다면, 특정 메소드를 구현해주도록 강제할 수 있습니다.

따라서 우리는 상속을 할 때는 부모클래스를 추상클래스로 만들지 반드시 한 번쯤은 고민해봐야 합니다.









