## 타입 지정하기

> ### 특정 원시 타입만 지정하기

```
let name:string = 'james';   // name 변수에는 string 타입만 할당 가능.

```
<br />

> ### 객체의 value의 타입 지정하기


```

interface User {            // 지정하고자 하는 타입 모델 만들기.
  name: string,
  id: number
};

const user:User = {         // 지정한 모델에 맞춘 객체 생성, 만약 설정에 맞지 않을 경우 오류 발생.
  name: 'james',
  id: 1
};

```
<br />

> ### 함수 매개변수, 반환 값 타입 지정하기

```

interface User {            // 지정하고자 하는 타입 모델 만들기.
  name: string,
  id: number
};

function test1():User {      // User의 모델에 일치하는 객체만 반환 가능.
  ...
}


funtion test2(user: User) {  // 매개 변수로 들어간 객체는 모델과 형태가 일치해야 함.
  ...
}

```



> ### 특정 값만 할당할 수 있게 하기

```

type CurrentState = 'open' | 'close';

let currentState:CurrentState = 'open';

currentState = 'hi';                     <<< 'open', 'close'가 아니므로 오류 발생.

```

<br />
