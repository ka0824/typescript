## 기존 리액트를 타입스크립트로 변환하기

> ### 설치하기

```
npm install --save typescript @types/node @types/react @types/react-dom @types/jest
```

> ### 진행과정

- 설정 파일 생성하기
  - root 디렉토리에서 tsconfig.json 파일 생성

```
tsc --init
```

-----------------------------------------------------------

<br />

- ts, tsx로 확장자 바꾸기
  - jsx문이 있다면 tsx로 변경.
  - 따라서 component 파일은 tsx로, 일반 js 파일은 ts로 확장자 변경.
  - 확장자를 바꾼 이후에, import문에서 출처가 js로 설정 되어있었을 경우, 해당 출처도 ts, tsx로 수정.

------------------------------------------------------------

<br />

- redux의 액션 생성 파일 수정하기
  - 액션 함수가 반환하는 객체의 타입을 지정해 줌.

```
interface ChangeInput {
    type: 'CHANGE_INPUT'
    inputValue: string
}

interface ChangeAnswer {
    type: 'CHANGE_ANSWER'
    answer: string
}

interface ChangeGame {
    type: 'CHANGE_GAME'
}

export const changeInput = (inputValue):ChangeInput => {
    return {
        type: 'CHANGE_INPUT',
        inputValue
    }
}

export const changeAnswer = (answer): ChangeAnswer => {
    return {
        type: 'CHANGE_ANSWER',
        answer
    }
}

export const changeGame = ():ChangeGame => {
    return {
        type: 'CHANGE_GAME',
    }
}
```

------------------------------------------------------------

<br />

- reducer 파일 수정 하기
  - reducer가 반환하는 state 객체의 타입을 지정해 줌.

```
import initialState from './initialState';

interface State {
    inputValue: string,
    answer: string,
    isGameStart: boolean
}

const gameReducer = (state = initialState, action):State => {
    switch (action.type) {
        case 'CHANGE_INPUT':
            return {
                ...state,
                inputValue: action.inputValue
            }
        case 'CHANGE_ANSWER':
            return {
                ...state,
                answer : action.answer
            }
        case 'CHANGE_GAME':
            return {
                ...state,
                isGameStart: !state.isGameStart
            }
        default:
            return state;
    }
}

export default gameReducer;
```

---------------------------------------------------------

<br />

- 이미지 불러오는 모듈 추가 설정하기
  - import 문으로 이미지를 불러올 때는 추가 설정이 필요.
 
 ```
 src/type/image.d.ts
 
 declare module '*.jpeg';        // 사용하고자하는 이미지 확장자를 모두 추가.
 
 // 이미지 불러오는 모듈 설정 파일 생성
 
 
 tsconfig.json
 
 {
  "compilerOptions": {
    "target": "es2016",                             
    "module": "commonjs",                                
    "esModuleInterop": true,                             
    "forceConsistentCasingInFileNames": true,            
    "strict": true,                                      
    "skipLibCheck": true                                 
  },
  "include": [".src/type", "image.d.ts"]       << 해당 프로퍼티를 추가.
}
 
 ```

<br />

---------------------------------------------------------------------

- useRef()의 타입을 설정
  - useRef로 특정 태그를 선택했을 경우, "HTMLInputElement"를 추가.
  
```
const gameNotice = useRef<HTMLInputElement>(null);
  
<div className="game-result" ref={gameNotice}>게임을 시작할까요?</div>
  
```
  
```
