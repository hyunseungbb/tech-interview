# Android



### 안드로이드 생명주기

- Created 
  - onCreate() 콜백함수가  실행
  - 액티비티가 생성되는 상태 
- Started
  - onStart() 콜백함수가 실행
  - 액티비티가 포그라운드에 보내지는 상태, 이때 사용자에게 표시된다.
- Resumed
  - onResume() 콜백함수가 실행
  - 포그라운드에 액티비티가 표시되는 상태, 이 때 앱이 사용자와 상호작용할 수 있다.

- Paused
  - onPause() 콜백함수가 실행
  - 여러 앱이 멀티 윈도우 모드에서 수행될 때, 일부 이벤트가 앱 실행을 방해할 때
  - 구성요소가 포그라운드에 있지 않을 때 실행할 필요없는 기능을 onPause()안에서 중단할 때 주로 사용한다.
- Stopped
  - onStop() 콜백함수 실행
  - **액티비티가 완전히 보이지 않게되면 호출**된다.
- Destroyed
  - 액티비티가 소멸된 상태
  - 소멸되기 직전 onDestroy()를 호출한다.



### 안드로이드 4대 컴포넌트

액티비티, 컨텐트 프로바이다, 브로드캐스트 리씨바, 서비스



### Activity, Fragment란?

- Activity와 Fragment의 생명주기 비교
- Acitivty에 비해 Fragment의 장단점



### 아키텍처

- MVC, MVP, MVVM 비교



### 코틀린

- 코틀린과 자바 비교, 장단점
- 함수형 프로그래밍이란? 코틀린에서는 함수형 프로그래밍을 어떻게 사용할 수 있나



### 코루틴

- 코루틴의 특징
- 코루틴의 suspend가 프로세스에도 있나?



### 비동기로 처리한 작업을 UI에 표시하기 위해 어떤 일이 필요한 지 설명해주세요.



### `onActivityResult`는 왜 deprecated 되었을까요?

### `ViewGroup` 내에 선언한 `View` 들에 `onClickListener` 를 선언할 경우 안드로이드가 이벤트를 어떻게 핸들링하는지 설명해 주시기 바랍니다.

### systrace 가 뭐고, 결과 분석은 어떻게?

### Memory leak 을 유발하는 coding pattern?

### Dagger 를 왜 쓸까요? 다른 대안은 없나요?

### Android HAL(Hardware Abstraction Layer) 에 대해 설명해주세요.



### 이모저모

- `kotlin-kapt` 플러그인
  - 코틀린에서 Java의 Glide나 Dagger의  Annotation Processing을 사용하기 위해서 사용하는 플러그인
- ktx
  - 


