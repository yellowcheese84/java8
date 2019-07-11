# Iterator, ListIterator, Enumeration

Iterator, ListIterator, Enumeration 모두 컬렉션에 저장된 요소를 접근하는데 사용되는 인터페이스

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

## ListIterator와 Enumeration
* Enumeration : Iterator의 구버전
* ListIterator : Iterator에 양방향 조회기능 추가(`List를 구현한 경우만 사용 가능`)

Java API 문서의 설명 중에서 `선택적 기능(optional operation)`이라고 표시된 메서드는 반드시 구현하지 않아도 된다.
ex) Iterator 인터페이스를 구현하는 클래스에서 remove()

그렇지만 인터페이스로부터 상속받은 추상메서드는 반드시 구현을 해야하기 때문에 아래와 같이 만들어 주는 것이 좋다.
```java
    public void remove() {
        throw new UnsupportedOperationException();
    }
```

* remove 메서드를 사용하는 경우 유의사항
```text
Iterator의 remove()는 특정위치의 요소를 삭제하는 것이 아니라 읽어 온 것을 삭제하기 때문에 
단독으로 쓰일 수 없고, next() 호출 후에 사용할 수 있다. next()의 호출 없이 사용하게 되면 IllegalStateException이 발생한다.
```




