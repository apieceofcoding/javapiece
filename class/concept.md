# 클래스의 구성

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
    String brand;
    int year;
}
```

위의 `brand`와 `year`는 `Car` 클래스의 멤버 변수입니다.

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

\
