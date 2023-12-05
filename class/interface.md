# 인터페이스(interface)



### 인터페이스

#### 인터페이스의 정의

인터페이스는 메서드의 시그니처(이름, 매개변수, 반환 값)만을 정의하며, 구현 내용을 제공하지 않는 객체 지향 프로그래밍의 개념입니다. 인터페이스는 `interface` 키워드를 사용하여 정의하며, 다음과 같은 특징을 가집니다:

* 모든 메서드는 암묵적으로 `public` 및 `abstract`입니다.
* 상수(static final) 필드를 가질 수 있습니다.

#### 인터페이스의 구성

인터페이스는 다음과 같이 구성됩니다:

1. **메서드 시그니처(abstract method signatures):** 인터페이스는 메서드의 이름과 매개변수 타입, 반환 타입만을 정의합니다. <mark style="background-color:yellow;">메서드 몸체(구현 내용)는 이 인터페이스를 구현하는 (implements) 객체에서</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">**반드시 구현**</mark><mark style="background-color:yellow;">해야 합니다.</mark>
2. **상수 필드(static final fields):** 인터페이스 내에서 선언한 필드는 상수로 취급되며, 암묵적으로 `public`, `static`, `final` 특성을 가집니다.



#### 인터페이스 사용예제

아래 예제는 `Transport` 인터페이스를 정의하고, `Car`와 `Bicycle` 클래스에서 이 인터페이스를 구현한 사용 예제입니다.

```java
interface HeadLight {
    void turnOn();
}
```

```java
interface FuelDoor {
    void fillUp(int fuel);
}
```

```java
interface Charger {
    void charge(int electricEnergy);
}
```

```java
class Vehicle {
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

<pre class="language-java"><code class="lang-java"><strong>class Car extends Vehicle implements HeadLight, FuelDoor {
</strong>    int fuel;

    Car(String name, int mileage, int speed, int fuel) {
        super(name, mileage, speed);
        this.fuel = fuel;
    }
    
    @Override
    public void turnOn() {
        System.out.println("내연차 전조등을 켭니다.");
    }
    
    @Override
    public void fillUp(int fuel) {
        System.out.println("연료를 채웁니다.");
        this.fuel += fuel
    }
}
</code></pre>

```java
class ElectricCar extends Vehicle implements HeadLight, Charger {
    int batteryAmount;

    ElectricCar(String name, int mileage, int speed, int batteryAmount) {
        super(name, mileage, speed);
        this.batteryAmount = batteryAmount;
    }
    
    @Override
    public void turnOn() {
        System.out.println("전기차 전조등을 켭니다.");
    }
    
    @Override
    public void charge(int electricEnergy);
        System.out.println("배터리를 충전합니다.");
        batteryAmount += electricEnergy;
    }
}
```

상속은 is-a 관계에 적합한 반면,

* 내연차는 운송수단이다.
* 전기차는 운송수단이다.

인터페이스는 has-a 관계에 적합합니다.

* 내연차는 전조등, 주유구를가진다.
* 전기차는 전조등, 충전기를 가진다.



```java
List<HeadLight> headLights = new ArrayList<>();
headLights.add(new Car("내연차", 100, 0, 20));
headLights.add(new ElectricCar("전기차", 50, 0, 70));

for (HeadLight headLight: headLights) {
    headLight.turnOn();
}
```

아래 코드를 실행시켜보면 아래 결과가 나옵니다.

```
내연차 전조등을 켭니다.
전기차 전조등을 켭니다.
```

headLights 에 자동차와 자전거를 담는 것이 이상해보이나, '전조등 기능을 가진 것들' 을 담는다고 생각하면 이치에 맞습니다. 그래서 인터페이스명을 `HeadLightable` , `Fillable`, `Chargable` 등 `-able` 을 붙여 짓기도 합니다.



이렇게 인터페이스는 각 클래스가 가진 기능에 대해 명시하는 기능을 하며,

구현체가 메소드를 강제적으로 구현해야 하기 때문에, 초반 인터페이스 설계가 아주 중요합니다.









