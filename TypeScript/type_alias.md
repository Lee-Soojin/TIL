# 타입 엘리어스 ( Type Alias )

## 타입 엘리어스

**타입 엘리어스**는 새로운 타입을 정의할 수 있다. 직접 이름을 부여하여 타입으로 지정을 할 수가 있는 것이다.

```ts
type Letter = string;
const message: Letter = "Hi";
const name: Letter = "Soojin";

type Count = number;
const sequence: Count = 1;
```

위의 경우는 Letter라는 타입을 string type과 동일한 타입으로 정의한 것이다.

또한 object 형태로도 정의가 가능하다.

```ts
type User = {
    name: string;
    age: number;
    id: string;
};

const user1 : User ={
    name: "Soojin,
    age: 5,
    id: sj123,
};
```

### String Literal Types

문자열을 타입으로 지정하는 것이다.

```ts
type Character = "Dooly";
let character = Character;
character = "Pororo"; // Error!
type JSON = "json";
const json: JSON = "json";
```

위의 예시처럼 변수나 매개변수에 타입 선언을 이용하여 정확한 값을 지정해 주는 것이다. string 이외에 number, boolean 등 여러타입도 가능하다.
리터럴 타입에 의해 값이 정해진 변수에 다른 값을 설정하려할 경우 에러가 발생한다.
