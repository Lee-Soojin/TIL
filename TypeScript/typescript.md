# TypeScript 타입스크립트

## **타입스크립트**

![TypeScript](../img/Typescript_logo.png) <br>
마이크로소프트사에서 만든 **자바스크립트의 슈퍼셋**인 **오픈 소스 언어**이다.
타입스크립트에서 원하는 타입을 정의하고 프로그래밍을 하면 자바스크립트로 컴파일되어 실행된다. 자바스크립트의 엔진을 이용해 더 큰 application을 만들 수 있는 언어이다. 모든 운영체제, 모든 브라우저, 모든 호스트에서 이용가능한 **오픈 소스 언어**이다. 클라이언트 사이드와 서버 사이드를 한 개발에 사용할 수 있다. <br>
자바스크립트는 dynamically typed 언어로 프로그램이 동작할때 타입이 결정되는 위험함이 존재한다.
그와 달리 타입스크립트는 Statically Typed 언어로 코딩을 할때 타입이 결정이 되는 정적인 타입 언어 이다.

타입스크립트에서 타입을 적는것은 optional이다.

### **Statically Type**

컴파일러 과정에서 타입이 결정되고 확인이 된다.

### **Dynamically Type**

런타임에서 타입이 결정되고 확인이 된다.

## **장점**

### **안정성**

자바스크립트는 타입이 불분명하여 가독성, 코드 이해성이 떨어진다. 또한 사용자가 어플리케이션을 사용하는 도중에 오류가 발생할 수 있다.
타입스크립트는 실시간으로 오류를 알아내고 보완할 수 있기 때문에 비교적 안정적이다.

### **강력한 객체지향 프로그래밍 가능**

타입스크립트는 강력한 객체지향 프로그래밍이 가능하다. <br>

#### _객체지향 프로그래밍의 특징_

- 객체 위주의 모듈성있는 코드 작성
- 모듈별로 원하는 것은 재사용 가능
- 객체 단위의 확장성이 높음
- 유지보수성이 높음

## **Composing Types**

### Unions

한 개 이상의 다른 타입을 선언할 수 있다.

```ts
function getLength(obj: string | string[]) {
  return obj.length;
}
```

위의 예시에서는 type을 string과 array로 선언하였다.

변수의 타입을 알기 위해서 **typeof**를 사용하면 된다.

### Generics

Generics는 변수를 타입의 형태로 선언할 수 있다.

```ts
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;
```

가장 흔한 예시로는 위와 같은 array가 있다. array는 generic이 없는 경우에는 배열에 아무 것이나 포함할 수 있다. generic이 있는 array는 담고 있는 변수만 describe할 수 있다.
