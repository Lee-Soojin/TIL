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
    console.log("๐ก Lights on");
  } else {
    console.log("๐ Lights off");
  }
}
```

์์ ๊ฐ์ด type ์ ์ ์ result์ string ๊ฐ์ ํ ๋นํ๋ฉด LightsOn์ด๋ ํจ์์์ ๊ทธ result๊ฐ์ ๋ฐ์ ๊ทธ์ ๋ฐ๋ฅธ ๋์์ ํ ์์๋ค.

LightState๋ผ๋ ํ์์ result๋ฅผ ๊ฐ์ง onState ์ offState๋ฅผ ์ด์ฉํด ์ ๋์จ ํ์์ผ๋ก ์ค์ ํจ์ผ๋ก์จ ์กฐ๊ฑด๋ฌธ์ ์ด์ฉํด result ๊ฐ์ ๋ฐ๋ฅธ ๊ฐ๊ธฐ ๋ค๋ฅธ ๋์์ ์คํํ  ์ ์๋ค.
