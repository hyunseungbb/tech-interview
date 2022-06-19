# 메모리 Leak을 유발하는 코딩 패턴

### Garbage Collection

- GC의 수집 단계

  1. 메모리에 있는 모든 객체 참조를 나열해서 참조가 있는 활성객체를 표시
  2. 1에서 표시가 되지 않는 객체들을 메모리에서 제거
  3. 살아있는 객체를 재정렬

- GC의 장점

  - 개발자가 명시적으로 메모리를 관리할 필요가 없다는 장점이 있다.

  - 잘못된 메모리 참조로 인한 앱의 크래시, 메모리 해제를 하지 않아 힙 메모리가 증가하는 가능성을 줄여준다.

- GC의 한계점
  - 객체 혹은 메소드는 강한 참조로 연결되어 있지 않은 경우에만 GC의 대상이 될 수 있다. 즉, 자신을 참조하고 있는 객체가 있는 경우 GC는 메모리 해제하지 않는다.
  - 즉, 완전하지는 않기 때문에 메모리 누수가 발생하는 경우를 파악하고 있어야 한다.



### 메모리 Leak

모든 연관 참조가 범위를 벗어나기 전에 할당한 메모리를 해제하지 않는 경우에 발생한다.



## Android

- 안드로이드에서의 가비지 콜렉터

  - 기존 호출 + Android 런타임에서 메모리가 부족할 때마다 호출된다.
  - 가비지콜렉터가 호출되는 순간 안드로이드의 UI렌더링이나 이벤트를 중단시킨다.
  - 

- 안드로이드에서의 메모리 누수란?

  - 일반적으로 Activity 등 생명주기 구성요소가 소멸하기 전에 할당된 메모리를 해제하지 않는 경우 발생한다.
  - Acitivty와 같은 context는 누수될 경우 context가 가리키는 많은 참조(뷰, 각종 자원) 또한 누수된다. 메모리가 초과되면 강제로 메모리를 해제시키는 안드로이드 특성 상 누수가 많이 발생하면 가용메모리가 전부 소진되거나, Out of Memory의 결과로 크래시를 유발할 수 있다.
  - Acitivty의 `onDestroy()` 메서드가 호출되면 보통 메모리 회수가 이루어지지만, 액티비티 객체가 강한참조로 연결되어 있는 경우 GC 대상이 되지 않아 메모리 릭이 발생할 수 있는 것이다. 

- 안드로이드에서 메모리 누수가 발생하는 경우

  - 생명주기 구성요소나 객체가 소멸하기 전에 할당된 메모리를 해제하지 않는 경우

    - 생명주기 구성 요소를 static 리소스로 관리하는 경우

      1. 정적 액티비티
      2. 정적 뷰
      3. INNER CLASS
      4. ANONYMOUS CLASS

    - 액티비티에서 강한참조로 연결된 스레드가 액티비티의 수명보다 오래 지속되는 경우

      5. HANDLER
         - 액티비티가 종료되기 전에 핸들러의 메시지 큐에 등록된 메시지가 모두 처리되지 않으면 메모리 누수가 발생할 수 있다.

      6. 스레드
      7. 타이머

    - 싱글톤 객체 혹은 ViewModel(생명주기가 더 긴 녀석들)에서 Activity나 Fragment의 context를 참조하는 경우

  - 안드로이드에는 메모리 릭 디버깅을 위해 메모리 프로파일러를 지원해준다.

   

## Python

- reference count of GC

- 레퍼런스 카운트
  - 장점 : 간단하고 빠름.
  - 동적 메모리가 참조될 때마다 count -> 확 느려지는 게 없다.
  - 단점 
    - 순환참조로 인한 메모리 릭 발생 위험
    - 각 객체에 대한 카운트 저장 공간 필요. Space Overhead
    - speed overhead
    - requires atomicity
    - not real-time

- Python Memory Manager



## Java

- 가비지 컬렉션
  - 장점 
    - 개발자가 명시적으로 메모리를 관리할 필요가 없다는 장점이 있다.
  - 단점
    - 정확한 동작 시점을 알 수 없다. 
    - 동작할 때 JVM 실행 정지-> 사용자 버벅임
      - ios가 잘 버벅이지 않는 이유 - 레퍼런스 카운팅을 써서



## Reference

- https://shinjekim.github.io/android/2019/11/01/Android-context%EB%9E%80/
- https://blog.mindorks.com/understanding-context-in-android-application-330913e32514

- https://d2.naver.com/helloworld/1329
-  https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html
