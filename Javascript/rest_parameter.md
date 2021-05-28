# Rest Parameter

Rest Parameter 는 정해지지 않은 인수를 배열로 나타낼 수 있게 한다. 가변 인자 함수를 구현할때 사용한다.

```js
function sum(...Args) {
  return Args.reduce((a, b) => a + b);
}

console.log(sum(1, 2, 3)); // 6
```

위와 같이 ...을 이용하여 사용하는 것이다.

```js
function f(a, b, ...Args) {
  // ...
}
```

위와 같이 마지막 parameter에 ...을 써서 rest parameter로 이용할 수 있다. 그리하여 같은 타입의 반복되는 변수들을 일일이 정의해주지 않아도 된다.

Rest parameter는 Array 인스턴스로 배열에 쓰이는 sort, map, forEach, pop 등의 메서드가 적용될 수 있다.

```js
function Number(a, b, ...Nums) {
  console.log("a", a);
  console.log("b", b);
  console.log("Nums", Nums);
}

Number(1, 2, 3, 4, 5, 6, 7);

// a, 1
// b, 2
// Nums, [3,4,5,6,7]
```

위와 같이 마지막 인수는 배열을 가진다.
하나의 값만 가지더라도 배열을 가진다.

```js
Number(1, 2);

// a,1
// b,2
// Nums, []
```

위처럼 주어질 경우 Nums 인수를 제공하지 않았지만 빈 배열로 존재한다.

```js
function multiply(multiplier, ...theArgs) {
  return theArgs.map(function (element) {
    return multiplier * element;
  });
}

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

위는 mdn에서 주어진 예제입니다. multiply function은 들어온 인수와 배열의 값을 map에 의해 하나씩 곱하여 배열로 출력해주는 함수입니다.
즉 rest parameter는 첫번째 인수를 제외한 모든 parameter를 배열로 모으는 역할을 합니다.

실제 배열이 아닌 유사 배열인 _arguments 객체와 달리_ rest parameter는 실제 배열이다. arguments는 배열처럼 사용할 수 있으므로 length 속성과 index 속성이 있다. arguments는 함수의 모든 인수를 포함하지만 rest parameter는 함수의 마지막 인수만 포함한다.
