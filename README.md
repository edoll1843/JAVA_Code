![KakaoTalk_20210404_185933004](https://user-images.githubusercontent.com/45708825/113505159-0ce6d280-9578-11eb-9e77-771276e2ba1f.png)

# ArrayList
* 배열같은거지만 객체들이 추가되어 용량을 초과하면 자동으로 부족한 크기많큼 늘어남
* C++의 백터같이 쓰이지 않을까???
* vector는 동기화된 메소드로 구성되어어서 멀티 스레드가 동시에 할 수 없고 하나의 스레드가 실행을 완료해야만 다른 스레드들이 실행할 수 있다. 그래서 멀티 스레드 환경에서 안전하게 객체를 추가 삭제 가능.
* 벡터는 항상 동기화 된다. ArrayList의 기능은 벡터와 동일하나, 자동 동기화 기능이 빠져있고 옵션으로 있다. 그리고 벡터에 비해 속도가 더 빠르다.
* List클래스 ArrayList, Vector, LinkedList들은 동일한 함수를 사용한다.

```java

//선언//
ArrayList list = new ArrayList();   <--- 타입 미 설정 Object로 선언
ArrayList<Student> members = new ArrayList<Student>();  <--- 타입 설정 Student객체만 사용 가능 
ArrayList<Integer> num = new ArrayList<Integer>();      <--- 타입 설정 int만 사용 가능
ArrayList<Integer> num = new ArrayList<>();             <--- 뒷부분 타입은 생략 가능
ArrayList<Integer> num = new ArrayList<>(10);           <--- 초기 용량 지정
ArrayList<integer> num = new ArrayList<>(Arrays.asList(1,2,3)); <---생성시 값 추가

boolean add(E e)/ void add()
list.add(3)     <--- 값추가
list.add(null); <--- null값 추가 가능
list.add(1,10); <--- indext 1뒤에 10 삽입, index를 생략하면 맨 뒤에 추가된다. 중간에 하면 한칸씩 밀려남
// insert를 해야할 경우가 많다면 ArrayList보단 LinkedList를 활용하는게 좋음 

set(int index, E element)
주어진 인덱스에 저장된 객체를 주어진 객체로 바꾼다.

E remove(int index)
list.remove(1); <--- index 1 제거
list.clear();   <--- 모든 값 제거 

E get(int index)
list.get(0);    <--- index 0번째의 값에 접근 list[0] 이거 안된다. 해봤음

boolean contains(Object o)
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

# java.util.Arrays;
자바에서 배열이나 리스트를 정렬한다고하면 sort()를 쓴다.
Arrays클래스는 배열의 복사,정렬,검색과 같은 배열 조작 기능을 가지고 있다.

## 배열의 오름차순(String도 가능)
* 기본 타입 배열이나 String배열 가능
```java
int arr[] = {4,2,4,1};
Arrays.sort(arr);
```

## 배열의 내림차순(String은 기본 타입이 아님)
* Collections.reversOrder()를 써서해야한다.
* 기본타입아님!!!
* 기본타입 정렬할때는 기본타입의 배열을 래퍼클래스로 만들어 Comparator를 두번쨰 인자로 넣어줘야한다.
```java
Integer arr[] = {23,3,1,4};
Arrays.sort(arr,Collections.reversOrder());//기본 타입 아님

int arr[] = {23,1,3,2};
Arrays.sort(arr,Cllections.reversOrder()); // 기본 타입
```

## 배열 일부분만 정렬
Array.sort()의 매개값으로 배열,시작 index, 끝index(시작에서 끝index만큼의 갯수만큼 정려)를 넣어주면 일부분만 정렬 할 수있다.
```java
int arr[] = {4,23,33,15,17,19};
Arrays.sort(arr,0,4); ---> 0,1,2,3요소만 정렬 4,15,23,33,17,19
```


# 프로그래머스_java

```java
2021/04/05
두개 뽑아서 더하기

import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        HashSet<Integer> set = new HashSet<>();
        for(int i = 0; i<numbers.length; i++){
            for(int j =i+1; j<numbers.length; j++){
                set.add(numbers[i] +numbers[j]);
            }
        }
        ArrayList<Integer> arr = new ArrayList<>(set);
        Collections.sort(arr);
       //set.stream().sorted().mapToInt(Integer::intValue).toArray();
        int[] answer = new int[arr.size()];
        for(int i = 0; i<arr.size();i++)
            answer[i] = arr.get(i);
        return answer;
    }
}
```

```java
2021/04/06
K번째 수
import java.util.*;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int answer[] = new int[commands.length];
        ArrayList<Integer> temp = new ArrayList<>();
        for(int i =0; i < commands.length; i++)
        {
            ArrayList<Integer> arr = new ArrayList<>();
            for(int j = commands[i][0]; j<=commands[i][1]; j++)
            {
                arr.add(array[j-1]);
            }
            Collections.sort(arr); 
            temp.add(arr.get(commands[i][2]-1));
        }
      
        int size =0;
        for(var i : temp)
            answer[size++] = i; 
        return answer;
    }
}

public class javacodingtest{
    public static void main(String [] args)
    {
        Solution a = new Solution();
        int arr[] = {1,5,2,6,3,7,4};
        int commands[][] = {{2,5,3,},{4,4,1},{1,7,3}};
        int A[] = a.solution(arr,commands);
        for(var i : A)
            System.out.println(i);
    }
}
```

```java
2021/04/06
완주하지 못한 선수
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i =0;
        for(i = 0; i< completion.length; i++)
        {
            if(!participant[i].equals(completion[i]))
            {
                return participant[i];//C++이랑은 다르게 바로 반환이 안된다. 뭐가 잘못됐는지 몰라서 한참 헤맸다..
            }
        }
        return participant[i]; 
    }
}
```

```java
2021/04/06
모의고사 

import java.util.*;
class Solution {
    public int[] solution(int[] answers) {
        int[] count ={0,0,0};
        int one[] = {1,2,3,4,5};
        int two[] = { 2, 1, 2, 3, 2, 4, 2, 5};
        int three[] = {3,3,1,1,2,2,4,4,5,5,};
        ArrayList<Integer> temp = new ArrayList<>();
        for(int i =0; i <answers.length; i++)
        {
            if(one[i%(one.length)] == answers[i])
                count[0]++;
            if(two[i%(two.length)] == answers[i])
                count[1]++;
            if(three[i%(three.length)] == answers[i])
                count[2]++;
        }
        int max = count[0];
        for(int i =0; i<count.length; i++){
            if(count[i] > max){
               max = count[i]; 
            }
        }
        for(int i = 0; i<count.length; i++)
        {
            if(count[i] == max)
                temp.add(i+1);
        }
        int answer[] = new int[temp.size()];
        int size = 0;
        for(var i : temp)
            answer[size++] = i;
        Arrays.sort(answer);
        return answer;
    }
}
```

```java
2021/04/06
2016년

class Solution {
    public String solution(int a, int b) {
        String answer = "";
        int mon = 0, day = 0;
        int year[] = {31,29,31,30,31,30,31,31,30,31,30,31};
        String an[] = {"THU","FRI","SAT","SUN","MON","TUE","WED"};
        for(int i = 0; i< a-1; i++)
            mon += year[i];
        mon = mon+b;
        day = mon%7;
        answer = an[day];
        return answer;
    }
}

```

```java
2021/04/06
가운데 글자 가져오기
import java.util.*;
class Solution {
    public String solution(String s) {
        String answer = "";
        int len = s.length();
        if(len % 2 ==0)
            answer += s.substring(len/2-1,len/2+1);
        else
            answer += s.substring(len/2,len/2+1); // C++과는 다르게 (시작 인덱스, 끝 인덱스)의 형식이다.
        return answer;
    }
}
```

```java
2021/04/06
같은 숫자는 싫어
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        int[] answer = {};
        ArrayList<Integer> temp = new ArrayList<>();
        for(int i = 0; i< arr.length-1; i++)
        {
            if(arr[i] != arr[i+1])
                temp.add(arr[i]);
        }
        temp.add(arr[arr.length-1]);
        answer = new int[temp.size()];
        int size =0;
        for(var i : temp)
            answer[size++] = i;
        return answer;
    }
}
```
```java
2021/04/06
나누어 떨어지는 숫자 배열

import java.util.*;
class Solution {
    public int[] solution(int[] arr, int divisor) {
        int[] answer = {};
        ArrayList<Integer> tmp = new ArrayList<>();
        for(int i =0; i< arr.length; i++)
        {
            if(arr[i] % divisor ==0)
                tmp.add(arr[i]);
        }
        answer = new int[tmp.size()];
        if(tmp.size() ==0)
        {
            answer = new int[1];
            answer[0] = -1;
        }
        else
        {
            int size =0;
            for(int i : tmp)
                answer[size++] = i;
        }
        Arrays.sort(answer);
        return answer;
    }
}
