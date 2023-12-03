# 클래스와 객체의 개념

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
        System.out.println("차량이 출발합니다.");
    }
}
```

여기서 `Car` 클래스는 자동차의 템플릿을 정의하며, `name`와 `mileage`는 자동차의 속성을 나타내고, `drive()`는 자동차의 동작을 나타냅니다.



#### **객체 생성**

클래스를 기반으로 객체를 생성하기 위해서는 `new` 키워드를 사용합니다.

```java
Car myCar = new Car();

System.out.println(myCar.name); // null
System.out.println(myCar.mileage); // 0

myCar.name = "Hyundai";
myCar.mileage = 100;
System.out.println(myCar.name); // Hyundai
System.out.println(myCar.mileage); // 100

System.out.println(myCar); // 인스턴스가 저장된 주소
```

위 코드는 `Car` 클래스를 기반으로 `myCar`라는 자동차 객체를 생성합니다.

그 다음엔 객체의 멤버변수 값을 출력합니다. 기본값이 들어가 있습니다.

그 다음으로 멤버변수 값을 수정하여 변경된 멤버변수 값을 출력했습니다.

마지막으로, 객체 자체를 출력해봅시다. 그러면 객체(인스턴스)가 저장된 주소값을 출력하게 됩니다.



