# 클래스와 객체의 개념

### 클래스 **(Class)**

클래스의 기본 정의는 아래 예시와 같습니다.

```java
class Car {
}
```

`class` 라는 키워드, 클래스명(Car), 이어서 중괄호`{}`까지 열고 닫아주면 클래스 선언이 가능합니다.

###

### **멤버 변수와 메서드**

#### **멤버 변수 (Instance Variables)**

멤버 변수는 객체의 상태를 나타내는 변수로, 클래스 내부에 선언됩니다. 이 변수는 클래스 내의 모든 메서드에서 사용 가능합니다.

```java
class Car {
    String name;
    int mileage;
}
```

위의 `name`와 `mileage`는 `Car` 클래스의 멤버 변수입니다.

멤버변수는 통상 필드(field), 프로퍼티(property = 속성) 라고도 불립니다.



#### **메서드 (Methods)**

메서드는 클래스 내에서 정의된 동작을 수행하는 함수입니다. 다음은 `Car` 클래스의 `start()` 메서드의 예시입니다.

```java
class Car {
    void start() {
        System.out.println("차량이 출발합니다.");
    }
}
```

메서드는 통상 함수(function) 라고도 불립니다.





***

### **클래스와 객체**

클래스(Class)는 객체(Object)를 만들기 위한 템플릿이며, 객체는 클래스를 기반으로 실제로 생성된 인스턴스(Instance)입니다.&#x20;

여기서 인스턴스란 클래스가 실제 메모리(힙 영역)에 할당되어 실체화된 것을 의미합니다.

객체와 인스턴스는 주로 같은 의미로 사용됩니다.



#### **클래스**

클래스는 `class` 키워드로 정의됩니다.

```java
class Car {
    String name;
    int mileage;

    void start() {
        System.out.println(name + " 차량이 출발합니다.");
    }
}
```

여기서 `Car` 클래스는 자동차의 템플릿을 정의하며, `name`와 `mileage`는 자동차의 속성을 나타내고, `start()`는 자동차의 동작을 나타냅니다.



#### **객체 생성**

클래스를 기반으로 객체를 생성하기 위해서는 `new` 키워드를 사용합니다.

```java
Car myCar = new Car();
System.out.println(myCar.name); // null
System.out.println(myCar.mileage); // 0

myCar.name = "현대";
myCar.mileage = 10000;
System.out.println(myCar.name); // 현대
System.out.println(myCar.mileage); // 10000

System.out.println(myCar); // 인스턴스가 저장된 주소
```

위 코드는 `Car` 클래스를 기반으로 `myCar`라는 자동차 객체를 생성합니다.

그 다음엔 객체의 멤버변수 값을 출력합니다. 기본값이 들어가 있습니다.

그 다음으로 멤버변수 값을 수정하여 변경된 멤버변수 값을 출력했습니다.

마지막으로, 객체 자체를 출력해봅시다. 그러면 객체(인스턴스)가 저장된 주소값을 출력하게 됩니다.





***

여기까지 클래스의 기본적인 개념을 배우느라 고생하셨습니다.

아까 표에서 봤던 데이터를 클래스에 담아 출력해볼까요?

```java
Car[] cars = {
    new Car("현대", 10000),
    new Car("기아", 20000),
    new Car("테슬라", 5000),
    new Car("BMW", 15000),
    new Car("벤츠", 25000),
};
Car{name='현대', mileage=10000}
Car{name='기아', mileage=20000}
Car{name='테슬라', mileage=5000}
Car{name='BMW', mileage=15000}
Car{name='벤츠', mileage=25000}
```

예제는 위와 같이 만들 수 있지만, 우리는 `생성자(constructor)` 와 `toString() 메소드`를 공부해야합니다.

다음 장에서 만나볼게요!





