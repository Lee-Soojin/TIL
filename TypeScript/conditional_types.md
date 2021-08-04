# Conditional Types

```ts
interface Singer {
  sing(): void;
}

interface Bob extends Singer {
  performance(): void;
}

type idol = Bob extends Singer ? number : string; // number

type pop = Susan extends Singer ? number : string; // string
```

Conditional types은 삼항 조건 연산자 `(condition? trueExpression: falseExpression)`형식을 사용한다.

그리하여 위의 예제에서 Bob이 Singer를 extends하는것이 true일 경우 number 타입이 되고 그렇지 않으면 string타입이 된다.

위의 예제만 봐선 conditional types이 유용해 보이지 않을수 있다.
하지만 conditional types은 generic type과 함께 쓰면 유용한 것을 알 수 있다.

```ts
type Show<T> = T extends string ? boolean : number;

type Look = Show<string>; // boolean
```

위처럼 generic 타입을 사용해서 generic 타입을 통해 지정된 타입을 기준으로 타입을 결정할 수 있다.
