# ArrayList
* 배열같은거지만 객체들이 추가되어 용량을 초과하면 자동으로 부족한 크기많큼 늘어남
* C++의 백터같이 쓰이지 않을까???

```java

//선언//
ArrayList list = new ArrayList();   <--- 타입 미 설정 Object로 선언
ArrayList<Student> members = new ArrayList<Student>();  <--- 타입 설정 Student객체만 사용 가능 
ArrayList<Integer> num = new ArrayList<Integer>();      <--- 타입 설정 int만 사용 가능
ArrayList<Integer> num = new ArrayList<>();             <--- 뒷부분 타입은 생략 가능
ArrayList<Integer> num = new ArrayList<>(10);           <--- 초기 용량 지정
ArrayList<integer> num = new ArrayList<>(Arrays.asList(1,2,3)); <---생성시 값 추가

add()
list.add(3)     <--- 값추가
list.add(null); <--- null값 추가 가능
list.add(1,10); <--- indext 1뒤에 10 삽입, index를 생략하면 맨 뒤에 추가된다. 중간에 하면 한칸씩 밀려남
// insert를 해야할 경우가 많다면 ArrayList보단 LinkedList를 활용하는게 좋음 

remove()
list.remove(1); <--- index 1 제거
list.clear();   <--- 모든 값 제거 

get()
list.get(0);    <--- index 0번째의 값에 접근 list[0] 이거 안된다. 해봤음

contains()
list.contains(1); <--- list에 1이 있는지 검색 : true, flase, find()같은거지

indexOf()
list.indexOf(1);   <--- 1이 있는 index 반환한다. 없으면 -1; 이거 유용할듯
```


# HashSet
* 중복된 값을 허용 안한다.
* 순서를 보장 없음
* null 값 저장 가능
* 내부적으로 HashMap을 사용하여 데이터 저장

```java
Set<Integer> 변수명 = new HashSet<>();     <--- 선언

add()
* 인자를 저장
* 객체를 저장 할 때 객체가 Set에 저장되어있지 않다면 True리턴, 저장됐다면 Flase
public boolean add(E e)

remove()
* 인자로 전달된 객체를 Set에서 삭제
* 객체를 삭제할 때 객체가 Set에서 삭제됐으면 True, 아니면 False
public boolean remove(Object o)

removeAll()
* 인자로 받은 Collection에 저장된 아이템들을 HashSet에서 삭제
boolean removeAll(Collection<?> c) 
```





