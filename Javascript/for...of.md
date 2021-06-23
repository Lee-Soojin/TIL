# for... of

**for...of**는 반복가능한 객체(Array, Map, Set, String ...)에 대해서 반복하고 각 개별 속성값에 대해 실행되는 문이 있는 사용자 정의 반복 후크를 호출하는 루프를 생성한다.

```js
for (variable of iterable) {
  statement;
}
```

**variable**: 반복에 서로 다른 속성값이 variable에 할당된다.

**iterable**: 반복되는 열거가능한 속성이 있는 **객체**

### Array 에 대해 반복

```js
let nums = [1, 2, 3];

for (let value of nums) {
  console.log(value);
}

// 콘솔 로그 출력: 10 20 30
```

### String에 대해 반복

```js
let text = "hi";

for (let value of text) {
  console.log(value);
}

// 콘솔 로그 출력:
// "h"
// "i"
```

### Map에 대해 반복

```js
let map = new Map([
  ["a", 1],
  ["b", 2],
  ["c", 3],
]);

for (let entry of map) {
  console.log(map);
}

// 콘솔 로그 출력:
// [a,1]
// [b,2]
// [c,3]

for (let [key, value] of map) {
  console.log(value);
}

// 콘솔 로그 출력:
// 1
// 2
// 3
```

```js
let array = [1, 2, 3];

for (let item of array) {
  console.log(item);
}

// 출력 : 1, 2, 3

for (let item in array) {
  console.log(item);
}

// 출력: 0, 1, 2
```

**for...of 와 for...in의 차이**는
for...in은 객체 순환을 for...of는 배열 값 순환을 하는 것이다.

따라서 위의 예시에서 for...in 사용 시 배열도 객체이므로 키값에 해당하는 값이 출력된다. 즉 array의 index값이 출력된다.
