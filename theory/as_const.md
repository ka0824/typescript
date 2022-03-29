## as const

- 기존 const를 사용하면 참조형 타입의 경우, 값을 추가, 변경, 제거하는 것이 가능했음.
- as const를 덧붙이면 조회만 가능할 뿐, 참조타입일지라도 수정 불가능해짐.

<br />

> ### 사용 예시
```
const person = {
  name: 'james',
  age: 30
} as const;

person.country = 'america' // 해당 객체는 존재하는 값에 대한 조회만 가능하다는 에러 문구가 나옴.

```
