# 3. 조건문 (if, else, switch)

### 3.1 if 문

#### 단일 if 문

`if` 문은 조건이 참인 경우에 코드 블록을 실행합니다.

```java
int age = 20;

if (age >= 18) {
    System.out.println("성인입니다.");
}
```

<details>

<summary>결과</summary>

```
성인입니다.
```

</details>

#### if-else 문

`if-else` 문은 조건이 참일 때와 거짓일 때 각각 다른 코드 블록을 실행합니다.

```java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
} else {
    System.out.println("미성년자입니다.");
}
```

<details>

<summary>결과</summary>

```
미성년자입니다.
```

</details>

#### 중첩 if 문

`if` 문 안에 다른 `if` 문을 중첩하여 복잡한 조건을 처리할 수 있습니다.

```java
int age = 25;
boolean hasID = true;

if (age >= 18) {
    if (hasID) {
        System.out.println("성인이며 신분증이 있습니다.");
    } else {
        System.out.println("성인이지만 신분증이 없습니다.");
    }
} else {
    System.out.println("미성년자입니다.");
}
```

<details>

<summary>결과</summary>

```
성인이며 신분증이 있습니다.
```

</details>

###

### 3.2 else if 문

`else if` 문은 여러 조건을 순차적으로 판단할 때 사용됩니다.

```java
int score = 85;

if (score >= 90) {
    System.out.println("A 학점");
} else if (score >= 80) {
    System.out.println("B 학점");
} else if (score >= 70) {
    System.out.println("C 학점");
} else {
    System.out.println("D 학점");
}
```

<details>

<summary>결과</summary>

```
B 학점
```

</details>

###

### 3.3 switch 문

`switch` 문은 다중 조건을 처리할 때 사용되며, 특정 값에 따라 코드 블록을 실행합니다.

```java
int day = 3;
String dayName;

switch (day) {
    case 1:
        dayName = "월요일";
        break;
    case 2:
        dayName = "화요일";
        break;
    case 3:
        dayName = "수요일";
        break;
    default:
        dayName = "기타 요일";
        break;
}

System.out.println("오늘은 " + dayName + " 입니다.");
```

<details>

<summary>결과</summary>

```
오늘은 수요일 입니다.
```

</details>

\
