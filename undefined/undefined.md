# 접근제어자

\
자바의 중요한 주제 중 하나인 접근 제어자에 대해 자세히 알아보겠습니다.

자바의 접근 제어자는 **클래스, 생성자, 메서드, 변수**의 접근 범위를 제어하는 데 사용됩니다.&#x20;



접근 범위를 모두 열어놓고(public) 사용해도 코드가 동작하는데 문제될 부분은 없습니다.

하지만 접근 범위를 제어하는 이유는 코드 설계자가 이 코드를 사용하는 다른 개발자들에게 특정 규칙을 강제하기 위함입니다.&#x20;

여기서 규칙이란, 특정 생성자, 메소드, 변수는 내부에서만 사용할테니 다른 곳에서는 사용하지 말아달라는 것입니다. 이는 캡슐화와도 관련이 있으며, 객체 지향 프로그래밍에서 중요한 개념 중 하나입니다.&#x20;





## 클래스의 접근제어자

먼저 클래스 앞에 붙을 수 있는 접근제어자는 public, default 가 있습니다.

```java
class Counter {
}
```

위 예시처럼 아무 접근제어자가 없을 때 기본적으로(default) 같은 패키지 안에서만 해당 클래스를 접근, 사용할 수 있습니다.

```java
class Main {
    public static void main(String[] args) {
        Counter count = new Counter();
    }
}
```

참고로 현재 패키지 구조는 아래와 같습니다.

```
coding
ㄴ Counter.java
ㄴ Main.java
```

같은 coding 패키지(디렉토리라고 생각하셔도 좋습니다) 하위에 있으므로 Main 에서 Counter 를 사용할 수 있는 구조입니다.

하지만, 다른 패키지에서는 어떨까요?

```
coding
ㄴ Counter.java
ㄴ Main.java
piece
ㄴ Main2.java
```

piece 패키지에 있는 Main2 에서는 Counter 에 접근할 수 없습니다. 이 때 접근을 허락하려면 아래와 같이 Counter 에 `public` 접근제어자를 붙여주면 됩니다.

```java
public class Counter {
}
```

<pre class="language-java"><code class="lang-java">package piece;
<strong>
</strong>import coding.Counter;
<strong>
</strong><strong>class Main2 {
</strong>    public static void main(String[] args) {
        Counter count = new Counter();
    }
}
</code></pre>

위와 같이 piece 패키지의 Main2 클래스에서도 coding 패키지의 Counter 를 Import 하여 가져오고, 사용할 수 있습니다.

클래스의 접근제어자는 보통 public 으로 많이 구성되어있습니다. 다른 패키지에서 접근하여 사용되는 일이 빈번하기 때문입니다.&#x20;



## 필드, 메소드의 접근제어자

클래스의 접근제어자와 다르게 public, protected, default, private 이렇게 4종류로 구성됩니다.

참고로 여기서 클래스의 접근제어자는 모두 public 으로 설정하겠습니다.

또한 패키지 구성은 아래와 같습니다.

```
coding
ㄴ Counter
ㄴ ViewsCounter
ㄴ Main
piece
ㄴ LikesCounter
ㄴ Main2
```



### **public:** 동일 패키지, 다른 패키지 등 어디서나 접근 가능

<pre class="language-java"><code class="lang-java">package coding;
<strong>
</strong><strong>public class Counter {
</strong>    public int count;

    public void increment() {
        count++;
    }
}
</code></pre>

```java
// 동일 패키지
package coding;

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
    }
}
```

```java
// 다른 패키지
package piece;

import coding.Counter;

public class Main2 {
    public static void main(String[] args) {
        Counter counter = new Counter();
    }
}
```

* 어디서나 접근 가능 (매우 편안)

### **protected:** 동일 패키지 및 자식클래스에서 접근 가능

```java
package coding;

public class Counter {
    protected int count;
    
    protected void increment() {
        count++;
    }
}
```

```java
// 동일 패키지
package coding;

public class Main2 {
    public static void main(String[] args) {
        Counter counter = new Counter();
    }
}
```

```java
// 동일 패키지
package coding;

public class ViewsCounter extends Counter {
    public void incrementViews() {
        this.increment();
    }
    
    public void printViews() {
        System.out.println("조회수 " + count);
    }
}
```

```java
// 다른 패키지
package piece;

public class LikesCounter extends Counter {
    public void incrementLikes() {
        this.increment();
    }
    
    public void printLikes() {
        System.out.println("좋아요 " + count);
    }
}
```

* 다른패키지에서 접근불가능
* 하지만 다른패키지에 있는 자식클래스에서는 접근가능

### **default(기본):** 동일 패키지 내에서만 접근 가능

```java
package coding;

public class Counter {
    int count;
    
    Counter() {
    }
    
    void increment() {
        count++;
    }
}
```

```java
package coding;

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
    }
}
```

* 다른패키지에서 접근불가능
* 자식클래스에서 접근불가능

### **private:** 같은 클래스 내부에서만 접근 가능

<pre class="language-java"><code class="lang-java">package coding;
<strong>
</strong><strong>public class Counter {
</strong>    private int count;
    
    private Counter() {
    }
    
    private void increment() {
        count++;
    }

    public void setCount(int value) {
        count = value;
    }

    public int getCount() {
        return count;
    }
}
</code></pre>

* 동일패키지 내 다른클래스에서 접근이 불가능
* 다른패키지에서 접근불가능
* 자식클래스에서 접근불가능



| 접근 제어자      | 현재 클래스 | 동일 패키지 | 자식 클래스 | 다른 패키지 |
| ----------- | ------ | ------ | ------ | ------ |
| `public`    | ✔      | ✔      | ✔      | ✔      |
| `protected` | ✔      | ✔      | ✔      | ❌      |
| `default`   | ✔      | ✔      | ❌      | ❌      |
| `private`   | ✔      | ❌      | ❌      | ❌      |



접근제어자의 보통 관례 사용은 아래와 같습니다.

* 클래스 접근제어자는 대부분 `public` 을 사용하여 모든 패키지에서 접근할 수 있도록 공유합니다.
* 필드 접근제어자는 보통 `private` 을 사용하고 이를 접근하기 위해 public getter, setter 메소드를 사용합니다. (뒷단원참고)
* 외부에서 사용하는 필드(상수 등)는 `public` 을 사용합니다.
* 외부에서 사용하는 메소드 접근제어자는 `public`, 내부에서 사용하는 메소드 접근제어자는 `private` 을 사용합니다.
* 자식 클래스에서 부모클래스의 private 필드, 메소드 접근이 필요하면 `protected` 로 접근을 허용합니다.

다만 위 의견은 코드 설계자의 철학과 개발팀 규칙에 따라 충분히 다를 수 있습니다.





## 생성자의 접근제어자

추가로 생성자 또한 위와 같이 4종류의 접근제어자를 사용할 수 있고, 원리는 같습니다.

* 기본 생성자는 `public` 이 기본으로 붙어있습니다.
* 생성자를 같은 클래스에서만 호출하게 하려면 `private` 을 붙입니다.
* 같은 패키지에서만 생성자를 호출하게 하려면 아무것도 붙이지 않습니다. (`default`)
* 자식클래스에서도 생성자를 호출하게 하려면 `protected` 를 붙입니다.



