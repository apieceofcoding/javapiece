# 컬렉션 프레임워크

## Collection Framework

Java 컬렉션 프레임워크는 자료를 저장하고 관리하는 데 사용되는 자료구조와 알고리즘의 모음입니다.&#x20;

컬렉션 프레임워크는 데이터를 효율적으로 다룰 수 있는 다양한 클래스와 인터페이스를 제공합니다.

주요 인터페이스로는 List, Set, Map이 있습니다.



## List 인터페이스

List 인터페이스는 순서가 있는 데이터를 저장하고, 중복을 허용합니다.&#x20;

기본적으로 리스트 안 요소를 다루기 위해 add, get, set, remove 등의 메소드를 지원합니다.



### ArrayList

ArrayList는 List 인터페이스를 구현한 클래스 중 하나로, 크기를 동적으로 조정할 수 있는 **배열 기반의 자료구조**입니다. 데이터를 추가하고 삭제할 때, 데이터의 인덱스를 활용하는 것이 주요 특징입니다.

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<String> arrayList = new ArrayList<>();
        
        // 요소 추가
        arrayList.add("Apple");
        arrayList.add("Banana");
        arrayList.add("Cherry");
        
        System.out.println(arrayList); // [Apple, Banana, Cherry]
        
        // 요소 가져오기
        String first = arrayList.get(0);
        System.out.println(first); // Apple

        // 요소 수정하기
        arrayList.set(0, "Green Apple");
        System.out.println(arrayList.get(0)); // Green Apple
        
        // 요소 삭제
        arrayList.remove("Banana");
        
        System.out.println(arrayList); // [Apple, Cherry]
    }
}
```

ArrayList는 데이터를 순서대로 저장하고, 인덱스를 통해 원하는 위치의 데이터에 접근할 수 있어 데이터를 효과적으로 다룰 수 있습니다.



### LinkedList

ArrayList와는 달리 LinkedList는 **이중 연결 리스트**로 구현되어 있어 데이터의 추가 및 삭제가 더 빠르게 이루어집니다.&#x20;

```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<String> linkedList = new LinkedList<>();
        
        // 요소 추가
        linkedList.add("Apple");
        linkedList.add("Banana");
        linkedList.add("Cherry");
        
        System.out.println(linkedList); // [Apple, Banana, Cherry]
        
        // 요소 가져오기
        String first = arrayList.get(0);
        System.out.println(first); // Apple

        // 요소 수정하기
        arrayList.set(0, "Green Apple");
        System.out.println(arrayList.get(0)); // Green Apple
        
        // 요소 삭제
        linkedList.remove("Banana");
        
        System.out.println(linkedList); // [Apple, Cherry]
    }
}
```

LinkedList는 데이터를 중간에 삽입하거나 삭제하는 작업이 ArrayList에 비해 빠르며, 이러한 특성을 활용하여 데이터를 효과적으로 다룰 수 있습니다



***

## Set 인터페이스

Set 인터페이스는 중복을 허용하지 않는 데이터를 저장합니다.

요소를 관리하기 위해 add, remove, contains 등의 메소드를 지원합니다.



#### HashSet

&#x20;HashSet은 Set을 구현한 클래스 중 하나로, 중복된 값을 허용하지 않고, 순서를 보장하지 않습니다.

```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<Integer> numbers = new HashSet<>();
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        numbers.add(3);
        
        numbers.remove(2);

        for (int number : numbers) {
            System.out.println(number); // [1, 3]
        }
    }
}
```



***

### Map 인터페이스

Map 인터페이스는 키-값 쌍을 저장합니다.

키값쌍을 관리하기 위해 기본적으로 get, put, remove, containsKey 등의 메소드를 지원합니다.&#x20;



#### HashMap

HashMap은 Map을 구현한 클래스 중 하나로, 키를 통해 값을 검색할 수 있습니다.

```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        HashMap<String, Integer> scores = new HashMap<>();
        scores.put("Alice", 95);
        scores.put("Bob", 88);
        scores.put("Charlie", 73);

        int aliceScore = scores.get("Alice");
        System.out.println("Alice's Score: " + aliceScore);
    }
}
```





