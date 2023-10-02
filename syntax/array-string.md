# 5. 배열과 문자열 다루기

### 5.1 배열

#### 배열이란?

배열은 동일한 데이터 타입의 여러 값을 하나의 변수에 저장하기 위한 자료 구조입니다. 배열은 인덱스를 사용하여 각 요소에 접근할 수 있습니다.

#### 배열 선언과 초기화

배열을 선언하고 초기화하는 방법은 다음과 같습니다:

```java
// 배열 선언과 초기화
int[] numbers = new int[5];
numbers[0] = 1;
numbers[1] = 2;
numbers[2] = 3;
numbers[3] = 4;
numbers[4] = 5;
```

#### 배열 길이

배열의 길이는 `length` 속성을 사용하여 얻을 수 있습니다.

```java
int[] numbers = {1, 2, 3, 4, 5};
int length = numbers.length; // 5
```

#### 배열 요소 접근

배열의 요소에 접근할 때는 인덱스를 사용합니다.

```java
int[] numbers = {1, 2, 3, 4, 5};
int element = numbers[2]; // 3
```

###

### 5.2 문자열

#### 문자열 생성과 초기화

문자열을 생성하고 초기화하는 방법은 다음과 같습니다:

```java
// 문자열 생성과 초기화
String greeting = "Hello, World!";
```

#### 문자열 연결

문자열을 연결할 때는 `+` 연산자를 사용합니다.

```java
String firstName = "John";
String lastName = "Doe";
String fullName = firstName + " " + lastName; // "John Doe"
```

#### 문자열 길이

문자열의 길이는 `length()` 메서드를 사용하여 얻을 수 있습니다.

```java
String text = "Java Programming";
int length = text.length(); // 16
```

#### 문자열 비교

문자열을 비교할 때는 `equals()` 메서드를 사용합니다.

```java
String str1 = "apple";
String str2 = "banana";
boolean areEqual = str1.equals(str2); // false
```

#### 문자열 추출

부분 문자열을 추출할 때는 `substring()` 메서드를 사용합니다.

```java
String text = "Hello, World!";
String substring = text.substring(7); // "World!"
```



