# 인터섹션과 유니온 타입

## Union Type

유니온 타입은 OR 기능을 한다. 변수나 함수의 매개변수에 두개 이상의 데이터 형식을 사용할 수 있다.

```ts
type Season = "Spring" | "Summer" | "Fall" | "Winter";
function Day(season: Season) {
  console.log(season);
}
Day("Summer");
```

위와 같이 OR을 이용하여 Season이라는 타입에 하나가 아닌 여러개의 문자열을 선언해주어 사용할 수도 있다.

```ts
function print(letter: number | string) {
  console.log(letter.toUpperCase());
}
```

위와 같은 경우는 사용할 수 없는 경우이다. letter의 타입이 number | string 인데 string 타입일 경우에만 해당하는 메소드를 사용하였으므로 잘못되었다.

```ts
fuction print(letter: number| string) {
    if(typeof letter === "string") {
        console.log(letter.toUpperCase());
    } else {
        console.log(letter);
    }
}
```

위처럼 if를 사용하여 조건을 주는 경우엔 string에만 해당하는 toUpperCase 메소드를 사용할 수 있게 된다.

---

## Intersection Type

인터섹션 타입은 여러 타입을 하나로 결합하는 AND 기능을 한다.

```ts
type User = {
    id: string;
    password: number;
};

type Engineer = {
    name: string;
    age: number;
    program : () => void;
};

function Programming(person: User & Engineer) {
    console.log(person.name, person.id, person.program());

    Programming{{
        name: "jin",
        age: 5,
        id: "angel",
        password: 1234,
        program : () => {},
    }};
}
```

위와 같이 Programming이라는 함수의 매개변수 person은 User type과 Engineer type을 둘다 가지고 있다. 그리하여 함수를 불러올때 User, Engineer 의 내용을 다 불러와야 한다.
