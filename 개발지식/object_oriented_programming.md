# 객체 지향 프로그래밍

컴퓨터 프로그래밍의 패러다임 중 하나이다.
로직을 상태와 행위로 이루어진 객체로 만드는 것이다.

### 객체

변수와 메소드를 grouping 한 것이라 할 수 있다.

## 특징

- 자료 추상화 : 불필요한 정보를 숨기고 필요한 정보만 표현하여 프로그램을 간단하게 하는 것이다. 즉 비슷한 속성이나 기능을 묶어서 클래스의 이름을 붙이는 것이다.
- 상속 : 새로운 클래스가 기존 클래스의 자료와 연산을 사용할 수 있는 것이다.
- 다중 상속 : 클래스가 2개 이상의 클래스로 부터 상속받을 수 있는 것이다.
- 동적 바인딩 : 실행 시간 중, 실행 과정 중 발생할 수 있는 바인딩이다.

## 장점

- 재사용성: 남이 만든 클래스를 가져와서 재사용하거나 상속을 통해 확장할 수 있다.
- 유지보수가 쉽다: 어떤 부분을 수정하기 위해 절차지향 프로그래밍은 그 특정 부분을 찾아서 일일이 수정해야 한다. 하지만 객체 지향 프로그래밍은 클래스 내부의 변수나 메소드만 수정하면 된다.
- 대형 프로젝트에 용이: 클래스 단위로 개발하여 각자 업무 분담을 통해 프로젝트를 진행하기 용이하다.

## 단점

- 설계 시 많은 시간과 노력이 필요하다.
- 객체가 많은 경우엔 용량이 커진다.
- 처리 속도가 느리다.

## 기본 구성 요소

- 클래스 : 객체지향 프로그램의 기본적인 사용자 정의 데이터형이다. **같은 성격**을 지닌 속성과 행위를 변수와 메소드로 정의한 것이다.
- 객체 : 클래스에서 정의한 것을 토대로 실제 메모리상에 할당된 것이다.
- 메소드: 객체에 명령을 내리는 메세지라 할 수 있다.

### **캡슐화란?**

캡슐화는 코드를 재수정없이 활용하기 위한 것으로 기능과 특성의 모음을 클래스라는 캡슐에 분류해 넣는 것이다.

**[캡슐화의 목적]** <br>
캡슐화를 하는 이유는 정보은닉 때문이다. 외부에서 함부로 객체의 정보를 변경할 수 없도록 보호하는 것이다.
