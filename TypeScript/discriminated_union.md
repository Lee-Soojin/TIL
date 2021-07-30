# Disciminated Union Type

```ts
type onState = {
  result: "on";
};

type offState = {
  result: "off";
};

type LightState = onState | offState;

function LightsOn(state: LightState) {
  if (state.rseult === "on") {
    console.log("💡 Lights on");
  } else {
    console.log("🌚 Lights off");
  }
}
```

위와 같이 type 정의 시 result에 string 값을 할당하면 LightsOn이란 함수에서 그 result값을 받아 그에 따른 동작을 할수있다.

LightState라는 타입을 result를 가진 onState 와 offState를 이용해 유니온 타입으로 설정함으로써 조건문을 이용해 result 값에 따른 각기 다른 동작을 실행할 수 있다.
