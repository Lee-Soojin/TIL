# Mapped Types

mapped type은 이미 선언되어진 기존의 타입을 새로운 타입으로 변환해준다. map 함수의 기능처럼 동작하여 mapped 타입이라고 한다.

mapped type을 사용하면 map()함수처럼 기존 타입의 요소를 순차적으로 돌면서 지정한 타입 조건에 따라 변환시켜준다.

```ts
type Person = {
  name: string;
  job: string;
  married: boolean;
};

type Optional<T> = {
  [P in keyof T]?: T[P];
};

const JayB: Optional<Person> = {
  name: "JAYB",
  job: "singer",
};
```

위의 예제를 보면 Optional이라는 타입을 사용하여 `<T>` 에 주어지는 타입의 요소를 각각 순차적으로 돌면서 optional 타입으로 변경시켜준다. 그렇게 변경된 타입을 JayB라는 변수에 적용시켜주게된다. 그리하여 Person 타입의 `married` key의 value를 선언하지 않아도 error가 발생하지 않는다.

mapped type은 keyof를 이용하여 타입을 변환한다.

---

**-** 와 **+** 를 이용하여 type을 제거하거나 추가할 수 있다.

```ts
type RemoveReadonly<T> = {
  -readonly [P in keyof T]: T[P];
};

type readonlyBook = {
  readonly title: string;
  readonly sale: number;
};

type book = RemoveReadonly<readonlyBook>;
```

위처럼 `-readonly`로 주어진 타입의 요소를 돌면서 readonly를 제거한다. 결과적으로 type book은

```ts
type book = {
  title: string;
  sale: string;
};
```

위와 같이 변환된 것이다.

---

## as를 이용한 key re-mapping

```ts
type Getters<T> = {
  [P in keyof T as `get${Capitalize<string & P>}`]: () => T[P];
};

interface Person {
  name: string;
  age: number;
  location: string;
}

type LazyPerson = Getters<Person>;
```

_결과_:

```ts
type LazyPerson = {
  getName: () => string;
  getAge: () => number;
  getLocation: () => string;
};
```

위는 타입스크립트 사이트의 핸드북에 나와있는 예제이다. as를 이용하여 key들을 re-mapping하는 것이다.

as를 이용하여 key의 이름앞에 get을 추가하고 앞글자를 대문자로 만들었다. 그리고 arrow로 key의 value를 반환하는 형식으로 바꾸었다.

참고: 타입스크립트 핸드북 <https://www.typescriptlang.org/docs/handbook/2/mapped-types.html>
