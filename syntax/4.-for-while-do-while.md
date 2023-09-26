# 4. 반복문 (for, while, do-while)

### 4.1 for 문

#### 초기화, 조건, 증감식 활용

`for` 문은 초기화, 조건, 증감식을 이용하여 반복 작업을 수행합니다.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("반복 횟수: " + i);
}
```

<details>

<summary>결과</summary>

```
1
2
3
4
5
```

</details>

#### 중첩 for 문

`for` 문을 중첩하여 다양한 패턴의 반복 작업을 수행할 수 있습니다.

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        System.out.println("i: " + i + ", j: " + j);
    }
}
```

<details>

<summary>결과</summary>

```
i: 1, j: 1
i: 1, j: 2
i: 1, j: 3
i: 2, j: 1
i: 2, j: 2
i: 2, j: 3
i: 3, j: 1
i: 3, j: 2
i: 3, j: 3
```

</details>

###

### 4.2 while 문

#### 조건에 따른 반복

`while` 문은 조건이 참인 동안 반복 작업을 수행합니다.

```java
int count = 0;

while (count < 5) {
    System.out.println("카운트: " + count);
    count++;
}
```

<details>

<summary>결과</summary>

```
카운트: 0
카운트: 1
카운트: 2
카운트: 3
카운트: 4
```

</details>

#### 무한 루프와 탈출 조건

`while` 문을 사용하여 무한 루프를 생성하고, 탈출 조건을 설정할 수 있습니다.

```java
int number = 0;

while (true) {
    if (number >= 5) {
        break; // 탈출 조건
    }
    System.out.println("숫자: " + number);
    number++;
}
```

<details>

<summary>결과</summary>

```
숫자: 0
숫자: 1
숫자: 2
숫자: 3
숫자: 4
```

</details>

###

### 4.3 do-while 문

#### 조건 검사 후 반복

`do-while` 문은 코드 블록을 먼저 실행하고 조건을 검사하여 반복 작업을 수행합니다.

```java
int x = 0;

do {
    System.out.println("x: " + x);
    x++;
} while (x < 5);
```

<details>

<summary>결과</summary>

```
x: 0
x: 1
x: 2
x: 3
x: 4
```

</details>

\
