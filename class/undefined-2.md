# 생성자

### **기본 생성자 (Default Constructor)**

기본 생성자는 매개변수가 없는 생성자로, 클래스 내부에 별도로 정의하지 않아도 자바 컴파일러가 자동으로 생성해줍니다.

```java
class Car {
    String brand;
    int year;
}
```

위 처럼 정의한 클래스는 기본적으로 아래와 같이 기본 생성자가 있습니다.

```java
class Car {
    String brand;
    int year;
    
    // 기본 생성자
    Car() {}
}
```

그래서 우리가 아래처럼 기본생성자를 통해 객체를 생성할 수 있었습니다.

```java
Car myCar = new Car();
```



### **매개변수가 있는 생성자**

매개변수가 있는 생성자는 객체를 생성할 때 필요한 정보를 전달할 수 있도록 합니다.

대신 이 경우 원래 자동으로 정의된 `Car() {}` 기본 생성자는 자동으로 만들어지지 않습니다.

```java
class Car {
    String brand;
    int year;

    // 매개변수가 있는 생성자
    Car(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }
}
```

> 💡**this**
>
> 여기서 `this.brand` 는 위에 정의된 멤버변수 `String brand` 를 가리킵니다.
>
> 즉, `this` 키워드는 자기 자신 객체의 주소를 가리키는 포인터라고 생각하시면 됩니다.
>
> 생성자에서 매개변수로 받는 `brand` 와 멤버변수 `brand` 이름이 동일하기 때문에, 관례상 왼쪽에는 `this.brand` 로 표기하여 구별한 것입니다. .



이 생성자를 사용하여 객체를 초기화하려면 다음과 같이 호출합니다.

```java
Car myCar = new Car("Toyota", 2023);
```





### **주 생성자, 부 생성자**

위 예시처럼 보통 모든 필드를 매개변수로 받는 생성자를 <mark style="background-color:yellow;">주 생성자</mark>라고 하며,

이 외에 여러 생성자를 정의할 수 있고 이를 <mark style="background-color:green;">부 생성자</mark>라고 합니다.&#x20;

부 생성자는 생성자 오버로딩을 통해 다양한 매개변수 조합을 지원할 수 있습니다.

```java
class Car {
    String brand;
    int year;

    // 매개변수가 있는 생성자
    Car(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }

    // 부 생성자1
    Car(String brand) {
        this.brand = brand;
        year = 2023;
    }
}
```

이렇게 부 생성자를 정의하면, 객체를 다양한 방법으로 초기화할 수 있습니다.

```java
Car car1 = new Car("Toyota", 2023);  // 매개변수가 있는 생성자 호출
Car car2 = new Car();               // 부생성자 호출
```

부 생성자를 사용하여 클래스의 객체를 초기화하려면, 생성자의 매개변수에 전달할 값을 조절하면 됩니다. 이렇게 하면 클래스의 유연성과 재사용성을 향상시킬 수 있습니다.



부생성자는 아래와 같이 주생성자를 이용해서 정의하는 방법이 있습니다.

코드의 일관성을 확보하고, 중복을 방지할 수 있을 확률이 높아 이 방법을 더 권장합니다.

```java
class Car {
    String brand;
    int year;

    // 매개변수가 있는 생성자
    Car(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }

    // 부 생성자2
    Car(String brand) {
        this(brand, 2023);
    }
}
```

여기서 `this()` 는 위에 있는 생성자`Car(String brand, int year)`를 호출합니다.



