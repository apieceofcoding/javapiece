# 연산자와 표현식

### 2.1 산술 연산자

#### 더하기 (+)

더하기 연산자는 두 개의 숫자를 더하는 데 사용됩니다.

```java
int a = 5;
int b = 3;
int sum = a + b;
```

위 코드에서는 `a`와 `b`를 더하여 `sum`에 저장합니다. `sum`은 8이 됩니다.

#### 빼기 (-)

빼기 연산자는 숫자 간의 뺄셈에 사용됩니다. 예를 들어:

```java
int x = 10;
int y = 7;
int difference = x - y;
```

위 코드에서는 `x`에서 `y`를 빼서 `difference`에 저장합니다. `difference`는 3이 됩니다.

#### 곱하기 (\*)

곱하기 연산자는 숫자를 곱하는 데 사용됩니다. 예를 들어:

```java
int p = 4;
int q = 6;
int product = p * q;
```

위 코드에서는 `p`와 `q`를 곱하여 `product`에 저장합니다. `product`는 24가 됩니다.

#### 나누기 (/)

나누기 연산자는 숫자를 나누는 데 사용됩니다. 예를 들어:

```java
double dividend = 20.0;
double divisor = 4.0;
double quotient = dividend / divisor;
```

위 코드에서는 `dividend`를 `divisor`로 나누어 `quotient`에 저장합니다. `quotient`는 5.0이 됩니다.

#### 나머지 (%)

나머지 연산자는 나눗셈의 나머지 값을 구하는 데 사용됩니다. 예를 들어:

```java
int num1 = 17;
int num2 = 5;
int remainder = num1 % num2;
```

위 코드에서는 `num1`을 `num2`로 나눈 나머지를 `remainder`에 저장합니다. `remainder`는 2가 됩니다.

#### 복합 대입 연산자 (+=, -=, \*=, /=, %=)

복합 대입 연산자는 연산과 대입을 함께 수행합니다. 예를 들어:

```java
int total = 10;
total += 5; // total = total + 5;
```

위 코드에서는 `total`의 현재 값에 5를 더하여 `total`에 다시 저장합니다. `total`은 이제 15가 됩니다.



#### 증감연산자

값을 하나 올리고, 내리는 연산자는 간편하게 아래와 같이 사용할 수 있습니다.

```java
int i = 0;
i++; // 1
```

이는 아래와 같은 동작을 수행합니다.

```java
int i = 0;
i = i + 1 // 1
```

마이너스(-) 연산도 마찬가지 입니다.

```java
int j = 0;
j--; // -1
```

이는 아래와 같은 동작을 수행합니다.

```java
int j = 0;
j = j - 1 // -1
```



#### 후위연산자와 전위연산자

위와 같이 `i++` 처럼 `++` 연산자가 뒤에있으면 후위연산자라 하며,

`++i` 처럼 앞에있으면 전위연산자라고 합니다.

후위연산자는 모든 동작 후, 자신의 값을 증가시키지만, 전위연산자는 자신의 값을 먼저 변경시키고 다른 동작을 실행한다는 차이점이 있습니다.

아래 예제에서 쉽게 이 차이를 알 수 있습니다.

```java
int a = 0;
System.out.println(a++); // 0
System.out.println(a); // 1

int b = 0;
System.out.println(++b); // 1
System.out.println(b); // 1
```





### 2.2 비교 연산자

#### 크다 (>), 작다 (<), 크거나 같다 (>=), 작거나 같다 (<=)

비교 연산자는 두 값을 비교하여 논리적인 결과를 반환합니다.

```java
int x = 5;
int y = 8;

// 크다 (>), 작다 (<)
boolean isXGreaterThanY = x > y;   // false
boolean isXLessThanY = x < y;      // true

// 크거나 같다 (>=), 작거나 같다 (<=)
boolean isXGreaterOrEqual = x >= y;  // false
boolean isXLessOrEqual = x <= y;     // true
```

#### 같다 (==), 같지 않다 (!=)

동등 비교 연산자는 두 값을 비교하여 같음 또는 다름을 판단합니다.

```java
int a = 10;
int b = 10;

// 같다 (==)
boolean isEqual = a == b;   // true

// 같지 않다 (!=)
boolean isNotEqual = a != b; // false
```

###

### 2.3 논리 연산자

#### 논리 AND (&&)

논리 AND 연산자는 두 개의 조건이 모두 참일 때만 결과가 참입니다.

```java
boolean condition1 = true;
boolean condition2 = false;

boolean result = condition1 && condition2; // false
```

#### 논리 OR (||)

논리 OR 연산자는 두 개의 조건 중 하나 이상이 참일 때 결과가 참입니다.

```java
boolean condition1 = true;
boolean condition2 = false;

boolean result = condition1 || condition2; // true
```

#### 논리 NOT (!)

논리 NOT 연산자는 주어진 조건을 부정합니다.

```java
boolean condition = true;

boolean result = !condition; // false
```

###

### 2.4 삼항 연산자

#### 삼항 연산자의 구조

삼항 연산자는 조건식을 기반으로 참일 때와 거짓일 때 각각 다른 값을 반환합니다.

```java
int age = 18;
String message = (age >= 18) ? "성인" : "미성년자";
```

삼항 연산자는 조건에 따라 값을 선택적으로 할당할 때 효과적으로 사용됩니다. 위의 예시에서, `age`가 18 이상이면 "성인"을, 그렇지 않으면 "미성년자"를 `message`에 할당합니다.

\


