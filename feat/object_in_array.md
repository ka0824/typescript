## 배열 안에 객체 넣기

Array 뒤에는 <>가 들어감에 주의.

```

const list: Array[object] = [];  << 오류가 남

const list: Array<object> = []; <> 꺽쇠 안에 원하는 타입을 넣음.
const list: Array<any> = [];

```
