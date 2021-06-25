# 유틸리티 타입

## `Partial<T>`

T 타입의 부분 집합을 만족하는 타입을 정의한다.

**예시**:

```ts
inteface Todo {
    name: string;
    description: string;
    number: number;
};

function updateTodo(todo: ToDo, fieldsToUpdate: Partial<ToDo>){
      return {...todo, ...fieldsToUpdate};
  }

const todo = {
      name: 'study js',
      description: 'study array',
      number: 1,
  };

const partialTodo = updateTodo(todo, {
      description: 'play game',
  });

const update = updateTodo(todo, partialTodo);

```

이와 같이 partialTodo는 Partial 타입을 지정해주어 ToDo inteface의 description 부분만 정의해도 문제가 되지 않는다.

---

## `Pick<T, K extends keyof T>`

```ts
type Pick<T, K extends keyof T> = {
  [P in K]: T[P];
};
```

T 타입에서 속성을 선택하여 그 집합으로 K를 구성한다.

**예시:**

```ts
type User = {
  id: string;
  age: number;
  name: string;
  number: number;
};

type Customer = Pick<User, "id" | "name">;

function getUser(id: string): User {
  return {
    id,
    age: 12,
    name: "Susan",
    number: 2,
  };
}

function getCustomer(id: string): Customer {
  return {
    id: id,
    name: "Bob",
  };
}
```

Pick은 위와 같이 기존의 type에서 부분적으로 몇 개의 속성을 택하여 새로운 type을 만들어낸다.

---

## `Omit<T,K>`

```ts
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;
```

Omit은 T의 모든 속성에서 K를 exclude하여 pick한 타입을 만든다.
즉, 특정한 속성만 제거한 타입을 만들어내는 것이다.

```ts
type User = {
  id: string;
  name: string;
  age: number;
  address: string;
};

type Customer = Omit<User, "address">;

const person: Customer = {
  id: "angel123",
  name: "Peter",
  age: 17,
};
```

위와 같이 person이라는 변수에 Customer이라는 Omit type을 지정하여 User type에서 address 속성을 가지지 않도록 한다.

## `Readonly<T>`

```ts
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
```

Readonly는 T의 모든 property를 readonly 타입으로 구성한다. 즉, 생성된 타입을 재할당할 수 없는것이다.

```ts
type Todo = {
  name: string;
  description: string;
};

function display(todo: Readonly<ToDo>) {
  todo.name = "study"; // error!
}
```

readonly로 설정된 property는 값을 재설정하면 에러가 발생한다.

---

## `Record`

```ts
type Record<K extends keyof any, T> = {
  [P in K]: T;
};
```

Record는 property keys 는 K, property value는 T인 object Type이다.

```ts
type Movie = {
  title: string;
};

type Cinema = "director" | "company" | "date";

const marvel: Record<Cinema, Movie> = {
  director: { title: "Someone" },
  company: { title: "marvelStudio" },
  date: { title: "July 7" },
};
```

위처럼 marvel이라는 변수에 ` Record<Cinema, Movie>` 타입을 부여하였다. Cinema 타입의 property를 key로, Movie의 property를 value로 정의하는 타입을 갖게 되는 것이다.
