# Iterator, ListIterator, Enumeration

Iterator, ListIterator, Enumeration 모두 컬렉션에 저장된 요소를 접근하는데 사용되는 인터페이스
* Enumeration : Iterator의 구버전
* ListIterator : Iterator의 기능을 향상

## Iterator
컬렉션 프레임웍에서는 컬렉션에 저장된 요소들을 읽어오는 방법을 표준화 하였는데,
이는 컬렉션에 저장된 각 요소에 접근하는 기능을 가진 Iterator 인터페이스를 정의하고,
Collection 인터페이스에는 Iterator를 반환하는 iterator()를 정의하고 있다.

```java
    public interface Iterator {
        boolean hasNext();
        Object next();
        void remove();
    }
    
    public interface Collection {
        ...
        public Iterator iterator();
        ...
    }
```

ex1) List와 Map 인터페이스를 구현한 객체의 Iterator 사용 예제 
```java
    public class IteratorTest {
        public void arrayListTest() {
            List list = new ArrayList();    // 다른 컬렉션으로 변경할 때는 이 부분만 고치면 된다.
            Iterator it = list.iterator();
            
            while(it.hasNext()) {
                System.out.println(it.next());
            }
        }
        
        public void hashMapTest() {
            Map<String, Object> map = new HashMap<>();
            Iterator it = map.keySet().iterator();  // Set 형태로 리턴하는 메소드 가능(keySet, entrySet)
        }
    }
```







