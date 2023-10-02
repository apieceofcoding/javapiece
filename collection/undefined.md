# 컬렉션 프레임워크 기능

## 컬렉션 프레임워크에서 주요 메서드

### **`add` 메서드**

`add` 메서드는 컬렉션에 요소를 추가하는 데 사용됩니다.&#x20;

```java
import java.util.ArrayList;

public class ArrayListAddExample {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>();
        
        // 요소 추가
        colors.add("Red");
        colors.add("Green");
        colors.add("Blue");
        
        System.out.println(colors); // [Red, Green, Blue]
    }
}
```



### **`remove` 메서드**

`remove` 메서드는 컬렉션에서 특정 요소를 제거하는 데 사용됩니다. 예를 들어, HashSet에서 요소를 제거하는 방법은 다음과 같습니다.

```java
import java.util.HashSet;

public class HashSetRemoveExample {
    public static void main(String[] args) {
        HashSet<Integer> numbers = new HashSet<>();
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        
        // 요소 제거
        numbers.remove(2);
        
        System.out.println(numbers); // [1, 3]
    }
}
```



### **`size` 메서드**

`size` 메서드는 컬렉션의 크기(요소의 개수)를 반환합니다. 예를 들어, ArrayList의 크기를 얻는 방법은 다음과 같습니다.

```java
import java.util.ArrayList;

public class ArrayListSizeExample {
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        
        // 크기 확인
        int size = fruits.size();
        System.out.println("Size: " + size); // Size: 3
    }
}
```



### **`isEmpty` 메서드**

`isEmpty` 메서드는 컬렉션이 비어 있는지 여부를 확인합니다. 예를 들어, HashSet이 비어 있는지 확인하는 방법은 다음과 같습니다.

```java
import java.util.HashSet;

public class HashSetIsEmptyExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        
        // 비어 있는지 여부 확인
        boolean isEmpty = set.isEmpty();
        System.out.println("Is Empty: " + isEmpty); // Is Empty: true
    }
}
```

####

## 컬렉션 프레임워크에서의 반복문 활용



### **for-each 루프**

for-each 루프는 컬렉션의 모든 요소를 반복적으로 접근할 때 사용됩니다. 아래는 ArrayList를 for-each 루프로 순회하는 예제입니다.

```java
import java.util.ArrayList;

public class ArrayListForEachExample {
    public static void main(String[] args) {
        ArrayList<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        
        // for-each 루프로 ArrayList 순회
        for (String name : names) {
            System.out.println(name);
        }
    }
}
```

####

## 컬렉션 프레임워크에서의 정렬

### **데이터 정렬**

데이터를 정렬하기 위해서는 `Collections.sort()` 메서드를 사용할 수 있습니다. 예를 들어, ArrayList를 오름차순으로 정렬하는 방법은 다음과 같습니다.

```java
import java.util.ArrayList;
import java.util.Collections;

public class ArrayListSortExample {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(5);
        numbers.add(2);
        numbers.add(7);
        
        // 데이터 정렬
        Collections.sort(numbers);
        
        System.out.println(numbers); // [2, 5, 7]
    }
}
```

###

### **Comparator 인터페이스 활용**

사용자 정의 정렬 기준을 적용하려면 Comparator 인터페이스를 구현하고 `Collections.sort()` 메서드에 Comparator 객체를 전달합니다. 아래는 문자열을 길이 순으로 정렬하는 예제입니다.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

public class CustomSortingExample {
    public static void main(String[] args) {
        ArrayList<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        
        // 길이 순으로 정렬하는 Comparator 구현
        Comparator<String> lengthComparator = (str1, str2) -> str1.length() - str2.length();
        
        // 데이터 정렬
        Collections.sort(names, lengthComparator);
        
        System.out.println(names); // [Bob, Alice, Charlie]
    }
}
```

이렇게 컬렉션 프레임워크에서 데이터 정렬을 할 때 Comparator 인터페이스를 활용하여 사용자 정의 정렬 기준을 적용할 수 있습니다.

