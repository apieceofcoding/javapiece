# 클래스는 왜 필요할까?



## 자료 저장 예제

예제로 자동차의 이름과 주행거리(km)를 저장해봅시다.

```java
String carName = "현대"
int carMileage = 10000
System.out.println(carName + " " + carMileage); // 현대 10000
```

위와 같이 간단하게 저장하고 출력할 수 있습니다.



그럼 이번에는 2대의 자동차의 이름과 주행거리를 저장해볼까요?

```java
String carName1 = "현대"
int carMileage1 = 10000
System.out.println(carName1 + " " + carMileage1); // 현대 10000

String carName2 = "기아"
int carMileage2 = 20000
System.out.println(carName2 + " " + carMileage2); // 기아 20000
```

위 처럼 가능합니다.



하지만 아래 표의 데이터를 입력하려면 우리는 어떻게 해야할까요?

| 자동차이름 | 주행거리  |
| ----- | ----- |
| 현대    | 10000 |
| 기아    | 20000 |
| 테슬라   | 5000  |
| BMW   | 25000 |
| 벤츠    | 15000 |

위 예제처럼 자동차이름과 주행거리 변수를 각각 5개씩 만들어 해결해야 합니다.

우리가 배운 것 중 이를 해결하기 위한 깔끔한 수단은 무엇일까요?



## 배열

배열을 사용하면 아래와 같이 해결 해볼 수 있습니다.

```java
String[] carNames = {"현대", "기아", "테슬라", "BMW", "벤츠"};
int[] carMileages = {10000, 20000, 5000, 25000, 15000};
for (int i = 0; i < 5; i++) {
    String carName = carNames[i];
    int carMileage = carMileages[i];
    System.out.println(carName + " " + carMileage);
}
//
현대 10000
기아 20000
테슬라 5000
BMW 25000
벤츠 15000
```

하지만, 이름과 주행거리를 각각 관리해야 한다는 점, 데이터의 크기 (5) 를 관리해야 한다는 점이 자료 관리를 어렵게 합니다.

여기서 점점 자동차 이름과 자동차 주행거리를 한 곳에서 관리할 수 있으면 좋겠다는 생각이 떠오릅니다.



그 해결방법으로 <mark style="background-color:orange;">클래스</mark>가 있습니다.

다음 장에서 살펴보겠습니다.

\
