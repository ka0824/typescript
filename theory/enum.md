## enum

- | 처럼 특정 변수에 할당할 특정 값 한정할 때 사용 가능.
- 혹은, 특정 값들에 id를 부여하여 사용하고 싶을 때 사용 가능.


<br />

> ### 사용 예시
```
enum Student {'kane', 'poong', 'chim'};   // 따로 지정하지 않으면 0부터 순차적으로 값 부여됨.
let tmTalker: Student = Student.poong     // 1이 할당됨.  && tmTalker에는 Student에 할당된 0, 1, 2 값만 할당 됨.

test1 = Student[1]         // poong이 할당됨.



enum Animal {'dog' = 'bow', 'cat' = 'meow'};
let bark: Animal = Animal.dog            // 문자열 'bow' 할당됨 && bark에는 'bow' 혹은 'meow'만 할당될 수 있음.
```
