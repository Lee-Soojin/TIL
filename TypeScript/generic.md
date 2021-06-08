# 제네릭 Generic

타입을 함수 parameter처럼 사용하는 것이 바로 제네릭이다. 함수나 클래스 호출시 원하는 타입을 지정해 줄 수가 있다. any를 사용하면 모든 타입이 any로 return 되기 때문에 좋지 않다. 따라서 우리는 generic을 사용하여 원하는 타입을 지정할 수 있다.

```ts
function GetValue<T>(value: T): T {
  return value;
}
```

`<T>` : **타입 매개변수, 제네릭 타입변수**

위와 같은 generic 문법을 이용한 함수는 함수를 호출할 때 타입을 넘겨줄 수 있다. <>이 괄호 안에 타입을 보통은 대문자 알파벳 한글자로 작성한다.

TEXT 라는 타입 매개변수의 경우 앞글자를 딴 T를 <T> 이렇게 간단히 작성하여 타입 매개변수를 작성할 수도 있다. T,U,V... 알파벳 순서대로 타입 매개변수를 작성해주는 방법도 많이 쓰는 방법 중 하나이다.

```ts
const number = GetValue<number>(123);
const obj = GetValue<object>({ name: "sj", age: 20 });
const boal = GetValue<boolean>(true);
```

이처럼 함수를 호출하면서 type을 number, object 등으로 넘겨줄수가 있다.

---

## 함수 제네릭

```ts
function PrintText<T>(text: T | null): T {
  if (text == null) {
    throw new Error("return text plz");
  }
  return text;
}

const message = PrintText("hi, nice to meet you");
```

위와 같이 함수에서 generic을 사용할 수 있다. message라는 변수는 PrintText 함수에 string을 넣어 호출했다. 따라서 type이 string으로 정해진다.
함수에서 사용할 경우, 함수명과 props, return 될 타입 자리에 generic type을 명시해주면 된다.
그리하여 외부에서 함수를 호출할 때 타입을 자유롭게 지정해줄 수 있다.

```ts
function sum<T extends number>(a: T, b: T): T {
  console.log(a + b);
  return a + b;
}
```

위와 같이 generic type을 다른 type으로 부터 extends 되는 형태로 사용할 수도 있다.
` <T extends string|boolean>`처럼 union타입으로 extends 된 타입을 정해줄 수도 있다.

---

## 클래스 제네릭

```ts
class GamePlay<T> {
  play(x:T, y: T): T,
  Item: T,
}

const round = new GamePlay<string>();
round.play = function(x,y) {return x+y};
round.Item = 'bomb';
```

클래스는 호출 시 객체를 만들 경우 사용할 타입을 `<T>` 자리에 지정해주면 된다.
