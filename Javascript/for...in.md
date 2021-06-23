# for...in

```js
const obj = { a: 1, b: 2, c: 3 };

for (const property in obj) {
  console.log(`${property}: ${obj[property]}`);
}
// 콘솔 로그 결과: "a:1" "b:2" "c:3"
```

```js
for (varaible in object) {...}
```

**variable**: 변수가 지정되는 자리이다.
**object**: 열거형 속성을 가진 객체

**for...in**문은 임의의 순서로 객체의 속성들에 대해 반복한다.
대입받은 변수를 이용하여 루프 안에서 객체의 enumrable한 property에 순차적으로 접근이 가능하다.
