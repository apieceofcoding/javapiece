# 정적 팩토리 메소드(Static factory method)

Java의 정적 팩토리 메소드는 클래스의 인스턴스를 생성하는 메서드로, 해당 클래스의 생성자 대신 사용할 수 있습니다.&#x20;

메소드 이름을 구체적으로 작성하여 사용하는 입장에서 용도를 명확히 파악할 수 있다는 장점이 있습니다.

## Static Factory Method 특징

### **명명 규칙**

Static Factory Method는 일반적으로 `of`, `from`, `valueOf,` `getInstance`, `newInstance` 등으로 작성할 수 있습니다. 또는 구체적인 이름을 직접 작성하여 메소드 사용의 이해를 도울 수 있습니다.

### **다중 생성자 대체**

생성자가 여러 개 있을 때, 각 생성자에 의미있는 이름을 부여하여 사용 가능한 생성자를 효과적으로 표현할 수 있습니다.

### **캐싱 및 재활용**

이미 생성된 인스턴스를 캐싱하거나, 특정 조건에 따라 재활용할 수 있습니다.

### **상위클래스 반환**

반환 타입은 인터페이스나 추상 클래스일 수 있으며, 실제 생성될 클래스는 하위 클래스에서 결정됩니다.



예시를 봅시다.

<pre class="language-java"><code class="lang-java"><strong>public class Car implements Vehicle {
</strong>    private String brand;
    private String model;
    private int year;

    // Private 생성자
    private Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    // 생성자 대신 사용 (명명 규칙)
    public static Car createCar(String brand, String model, int year) {
        // 추가적인 로직 수행 가능
        // 캐싱 또는 재활용 등의 처리 가능

        // 실제 생성은 private 생성자에서 이루어짐
        return new Car(brand, model, year);
    }

    // 캐싱 및 재활용을 고려한 예시
    private static final Map&#x3C;String, Car> carCache = new HashMap&#x3C;>();

    public static Car getCachedCar(String brand, String model, int year) {
        String key = brand + "-" + model + "-" + year;

        // 캐시에 이미 있는 경우 재활용
        if (carCache.containsKey(key)) {
            return carCache.get(key);
        } else {
            // 없는 경우 생성하고 캐시에 저장
            Car newCar = new Car(brand, model, year);
            carCache.put(key, newCar);
            return newCar;
        }
    }

    // 인터페이스를 반환하는 예시
    public static Vehicle createVehicle(String brand, String model, int year) {
        return new Car(brand, model, year);
    }
}

// 인터페이스 예시
interface Vehicle {
    // 인터페이스 메서드 정의
}
</code></pre>

위 예시에서 `Car` 클래스는 여러 정적 팩토리 메소드를 만들었습니다.&#x20;

* 첫 번째 메서드는 생성자 대신 사용하여 자신이 하는 일을 구체적으로 메소드명에 명시하였습니다.&#x20;
* 두 번째 메서드는 캐싱 및 재활용을 사용했습니다. 생성자에서는 항상 새로운 객체만 반환하므로, 위와 같이 할 수 없는 반면 정적팩토리 메소드에서는 위처럼 내가 원하는 로직을 집어넣을 수 있습니다.
* 세 번째 메서드는 인터페이스를 반환하여 사용하는 입장에서 다형성을 활용할 수 있도록 도울 수 있습니다. 이 외에도 필요하다면 상위 인터페이스가 아닌 다른 어떤 것이든 반환할 수 있습니다.



