![KakaoTalk_20210404_185933004](https://user-images.githubusercontent.com/45708825/113505159-0ce6d280-9578-11eb-9e77-771276e2ba1f.png)

# ArrayList
* 배열같은거지만 객체들이 추가되어 용량을 초과하면 자동으로 부족한 크기많큼 늘어남
* C++의 백터같이 쓰이지 않을까???
* vector는 동기화된 메소드로 구성되어어서 멀티 스레드가 동시에 할 수 없고 하나의 스레드가 실행을 완료해야만 다른 스레드들이 실행할 수 있다. 그래서 멀티 스레드 환경에서 안전하게 객체를 추가 삭제 가능.
* 벡터는 항상 동기화 된다. ArrayList의 기능은 벡터와 동일하나, 자동 동기화 기능이 빠져있고 옵션으로 있다. 그리고 벡터에 비해 속도가 더 빠르다.
* List클래스 ArrayList, Vector, LinkedList들은 동일한 함수를 사용한다.

# LinkedList
각 노드가 데이터와 포인터를 가지고 한줄로 연결되어 있는 방식의 자료구조이다.
- Node는 LinkedList에 객체를 추가하거나 삭제하면 앞뒤 링크만 변경
- 중간에 데이터를 추가나 삭제하더라도 전체의 인덱스가 밀리거나 당겨지지않는다.
- ArrayList에 비해서 추가나 삭제가 용이하다.
- 인덱스가 없기에 특정 요소에 접근하기 위해서는 순차 탐색이 필요
- 탐색/정렬을 자주 하면 배열
- 데이터 추가/삭제 많으면 LinkedList이용 하면 좋음

# vector
ArrayList와 동일한 내부구조이다. vector내부에 값이 추가되면 자동으로 크기가 조절된다.
vector는 동기화된 메소드로 구성되어있기 때문에 멀티 스레드가 동시에 이 메소드들을 실행할수없다.
즉 항상 동기화되는 특징이있다.

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
* 저장 순서가 유지 되지않는다.
* 순서를 보장 없음
* null 값 저장 가능
* 정렬없음
* 내부적으로 HashMap을 사용하여 데이터 저장

# TreeSet
* 중복 안됨
* 저장 순서 유지 안됨
* BST구조
* 왼쪽->오른쪽 순으로 읽어오면 오름차순 된 정렬 얻을수 있음.
* 주가 삭제 시간 걸리지만 정렬,검색에 좋음

```java
Set<Integer> 변수명 = new HashSet<>();     <--- 선언

add()
* 인자를 저장
* 객체를 저장 할 때 객체가 Set에 저장되어있지 않다면 True리턴, 저장됐다면 Flase
public boolean add(E e)

boolean contains(Object o)
* 주어진 객체가 저장되어있는지

remove()
* 인자로 전달된 객체를 Set에서 삭제
* 객체를 삭제할 때 객체가 Set에서 삭제됐으면 True, 아니면 False
public boolean remove(Object o)

removeAll()
* 인자로 받은 Collection에 저장된 아이템들을 HashSet에서 삭제
boolean removeAll(Collection<?> c) 
```
# Map
map은 키와 value로 구성된 객체를 저장.
* 키는 중복 안됨
* 값은 중복 가능
* 중복된 키들어오면 기존것은 없어지고 새로운것으로 대치됨]
* 키와 value는 한쌍

## HashMap
hashmap은 대표적인 map컬렉션
* map의 성질 그대로 가지고있음
* 키와 값은 모두 객체
* 값은 중복, 키는 중복 안됨

## TreeMap
TreeMap은 HashMap과는다르게 정렬이 된다고 볼수있다.
왼->오로 읽어오면 오름차순의 값을 알 수 있다.

```java
HashMap<String,String> Hash_map = new HashMap<String,String>(); <---생성
HashMap<String,String> Hash_map = new HashMap<>();              <--- 생략 가능

V put(K Key, V value)	주어진 키와 값을 추가하여 저장되면 값을 리턴합니다.
boolean containsKey(Object Key)	주어진 키가 있는지 확인합니다.
boolean containsValue(Object value)	주어진 값이 있는지 확인합니다.
Set<Map.Entry<K,V>> entrySet()	모든 Map.Entry 객체를 Set에 담아 리턴합니다.
Set<K> keySet()	모든 키를 Set객체에 담아서 리턴합니다.
V get(Object key)	주어진 키에 있는 값을 리턴합니다.
boolean isEmpty()	컬렉션이 비어있는지 조사합니다.
int Size()	저장되어 있는 전체 객체의 수를 리턴합니다.
Collection<V> values()	저장된 모든 값을 Collection에 담아서 리턴합니다.
void clear()	저장된 모든 Map.Entry를 삭제합니다.
V remove(Object Key)	주어진 키와 일치하는 Map.Entry를 삭제하고 값을 리턴합니다.
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

# String
```java
String str;
char[] sol = str.toCharArray();     <--- String을 char배열에 넣는 방법

String str = new String(sol);       <--- char배열 -> String
String a = String.valueOf(str)      <--- char배열 -> String

str.toString();                     <--- 출력이기도 하면서 반환도됨
str.charAt(i);                      <--- String을 하나씩 접근. 인덱스에 맞는 char접근. 반환형은 char이다.

String str = "010-1234-5678";
String[] mob = str.split("-");  <--- split함수는 입력받은 특정 문자를 기준으로 문자열을 나누어 배열에 저장하여 리턴한다.
String ret1 = mob[0];   <--- 010
String ret2 = mob[1];   <--- 1234
String ret3 = mob[2];   <--- 5678

String str = "abcd";
str.toUpperCase();          <--- 문자열을 모두 대문자로 변환
str.toLowerCase();          <--- 문자열을 모두 소문자로 변환

str.trim()              <--- 문자열의 양쪽에있는 공백을 제거하는 함수

String str = "123";
int to = Integer.parseInt(str);    <--- String -> int(기본 int형 반환임)
Integer to = Integer.valueOf(str);      <--- String -> int (래퍼 객체가 필요하면 이거)

int from = 123;
String to = Integer.toString(from); <--- int -> String



```
# Character

Character.

```java
boolean isDigit(char ch)        <--- 지정된 문자가 숫자인지 판별
boolean isLetter(char ch)       <--- 지정된 문자가 범용 문자인지 판별
boolean isLowerCase(char ch)    <--- 지정된 문자가 소문자인지 판별
boolean isUpperCase(char ch)    <--- 지정된 문자가 대문자인지 판별
boolean isLetterOrDigit(char ch)    <--- 지정된 문자가 문자인지 숫자인지 판별
boolean isSpaceChar(char ch)     <--- 문자가 스페이스인지 판별
char toLowerCase(char ch)       <--- 소문자로 변환
char toUpperCase(char ch)       <--- 대문자로 변환
String toString()               <--- String객체로 리턴한다.

```


# StringBuilder/StringBuffer
```java
String str;
StringBuilder sb = new StringBuilder(str);

sb.append(값)    <--- 뒤에 값을 붙인다.
sb.insert(인덱스,값)    <--- 특정 인덱스부터 값을 삽입한다.
sb.delete(index,index)  <--- 특정 인덱스부터 인덱스까지 삭제
sb.indexOf(값)           <--- 값이 어느 인덱스에 들어있는지 확인한다.
sb.substring(인덱스,인덱스)   <---값을 잘라온다.
sb.length()                 <--- 길이
sb.replace(인덱스,인덱스,값)            <--- 인덱스부터 인덱스까지 값으로 변경
sb.reverse()            <--- 리버스

```

# 프로그래머스_java

```java
2021/04/10
class Solution {
    public int solution(String s) {
        int answer = Integer.parseInt(s);    
        return answer;
    }
}
```
```java
2021/04/10
수박수박수박수박수박?
class Solution {
    public String solution(int n) {
        String answer = "";
        for(int i =0; i< n; i++)
        {
            if(i%2 == 0)
                answer += "수";
            else
                answer += "박";
        }
        return answer;
    }
}
```
```java
2021/04/10
서울에서 김서방 찾기
import java.util.*;
class Solution {
    public String solution(String[] seoul) {
        String answer = "김서방은 ";
        for(int i =0; i<seoul.length; i++)
        {
            if(seoul[i].equals("Kim") == true)
                answer += i+"에 있다";
        }
        return answer;
    }
}
```

```java
2021/04/10
문자열 다루기 기본

import java.util.*;
import java.lang.*;
class Solution {
    public boolean solution(String s) {
        boolean answer = true;
        if(s.length() != 4 && s.length() != 6)
            return false;
        for(char i : s.toCharArray())
        {
            if(!Character.isDigit(i))
                answer = false;
        }
        return answer;
    }
}
```
```java
2021/04/10
문자열 내 y와 p의 개수
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        int y_cnt =0, p_cnt =0;
        char s_arr[] = s.toCharArray();
        for(int a =0; a< s_arr.length; a++)
        {
            char i = s_arr[a];
            if(i == 'p' || i == 'P')
                p_cnt++;
            else if(i == 'y' || i == 'Y')
                y_cnt++;
        }
        return p_cnt == y_cnt ? true : false;
    }
}
```
```java
2021/04/10
문자열 내림차순으로 배치하기
import java.util.*;
class Solution {
    public String solution(String s) {
        char[] sol = s.toCharArray();
        Arrays.sort(sol);
        return new StringBuilder(new String(sol)).reverse().toString();
    }
}
```

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

```

```java
2021/04/07
체육복

import java.util.*;

class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
            int answer = 0;
            int arr[] = new int[n];
            for(int i =0; i< arr.length; i++)
                arr[i] = 0;
            for(int j = 0; j< lost.length; j++)
            {//잃어버린 학생 파악
                arr[lost[j]-1] += -1; 
            }
            for(int x = 0; x<reserve.length; x++)
            {//남아있는 학생 파악
                arr[reserve[x]-1] += 1;
            }
        for(int i = 0; i<arr.length; i++)
        {
            if(i == 0)
            {
                if(arr[1] >0)
                {    
                    arr[1] += -1;
                    arr[0] += 1;
                }
            }
            else if(i == arr.length-1)
            {
                if(arr[i-1] > 0)
                {
                    arr[i-1] += -1;
                    arr[i] += 1;
                }
            }
            else
            {
               if(arr[i] < 0)
               {
                   if(arr[i+1] > 0)
                   {
                       arr[i+1] += -1;
                       arr[i] += 1;
                   }
                   if(arr[i-1] > 0)
                   {
                       arr[i-1] += -1;
                       arr[i] += 1;
                   }
               }
            } 
        }
        for(int i =0; i< arr.length; i++)
        {
            if(arr[i] >= 0)
                answer++;
        }
        return answer;
    }
}
```

```java
2021/04/07
두 정수 사이의 합
class Solution {
    public long solution(int a, int b) {
        long answer = 0;
        if(a == b)
            return a;
        else
            for(int i = (a>b ? b:a) ; i<= (a>b? b:a); i++)
                answer += i;
        return answer;
    }
}
```

```java
2021/04/07
문자열 내 마음대로 정렬하기

import java.util.*;
class Solution {
    public String[] solution(String[] strings, int n) {
        String[] answer = {};
        ArrayList<String> arr = new ArrayList<>();
        for(int i = 0; i< strings.length; i++)
        {
            String temp = strings[i].charAt(n) + strings[i];
            arr.add(temp);
        }
        Collections.sort(arr);
        answer = new String[arr.size()];
        for(int i = 0; i< arr.size(); i++)
        {
            String tmp = arr.get(i);
                answer[i] = tmp.substring(1,tmp.length()); 
        }
        return answer;
    }
}
