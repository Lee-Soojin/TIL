# 서버사이드 렌더링이란?

**참고영상: 드림코딩 엘리님 영상 → <https://youtu.be/iZ9csAfU5Os>**

---

## 웹의 역사 🧾

### _1990년대_

static sites를 사용했다. 서버에 있는 html 문서들을 불러오는 형식으로 사이트가 동작되어졌다.
이러한 동작 형식 때문에 링크를 누르면 html 문서를 불러오는 동작을 다시 실행해야 하는 문제가 있었다.

### _1996년_

iframe 태그가 등장하였다. 또한 부분적으로 문서를 불러와 업데이트 하는 것이 가능해졌다.

### _1998년_

XMLHttpRequest API가 개발된다. 그리하여 JSON 등을 사용해 필요한 데이터만 서버에서 불러올 수 있게 되었다. Javascript를 이용해서 동적으로 html 을 업데이트 하는 것이 가능해졌다.

### _2005년_

AJAX라는 이름으로 위의 동작이 명칭되어진다. SPA(Single Page Application)이 점점 많아진다.

그 이후로 SPA 트렌드, 컴퓨터의 성능 발달, 커뮤니티 생성, 프레임워크(Angular, React, Vue ...)들의 등장 등의 이유로 **CSR(Client Side Rendering)** 시대가 시작된다.

---

## _CSR 이란_

**클라이언트 측이 주가 된다.** 서버는 *index.html*을 클라이언트 측에 보내준다. 이 index 파일에는 body 부분에 id='root'와 app.js를 선언한 것이 전부이다. 그리하여 사이트 구동 시 빈 html 화면에서 js 파일을 서버로 부터 받아 동작 시킨다.
이 *js 파일*에 프레임워크, 사이트 구현을 위한 소스코드들이 들어있다. 추가적으로 필요한 데이터도 서버에서 받아와서 사용자에서 제공하게 된다.

### CSR의 단점

- 사용자에게 사이트를 보여주기까지 시간이 상대적으로 오래 걸린다.
- SEO가 좋지 않다. html 파일이 비어있기 때문에 검색 엔진들이 사이트를 검색하는데 좋지 않은 환경을 지니고 있다.

---

## **SSR ( ✨Server Side Rendering✨)**

사이트 접속 시 서버에서 필요한 데이터를 가져와 html을 만든다. 그 후 html을 동적으로 보여주는 js 파일과 함께 클라이언트에게 제공한다. 그리하여 클라이언트는 서버로 부터 제공받은 html 문서를 사용자에게 바로 보여주게 된다.

### SSR 장점

- 페이지 로딩 속도가 빠르다.
- SEO가 좋다. 컨텐츠가 HTML에 담겨있기 때문이다.

### SSR 단점

- Blinking issue가 존재한다.
- 사용자가 많은 제품일수록 서버에 요청이 많아져 과부하가 걸리기 쉽다.
- js 파일을 아직 다 업데이트하지 못해 사용자의 입력에 동적으로 반응하지 않는 경우가 생긴다.

---

## SSG (Static Site Generation)

React 랑 Gatsby를 같이 사용해 정적인 사이트를 미리 생성해 서버에 배포해 놓을수 있다. 추가 데이터를 받아오거나 js파일을 받아 동적인 사이트 동작도 가능하다.

Gatsby뿐만 아니라 Next.js도 React와 함께 사용할 수 있다. *NEXT.JS*는 강력한 SSR과 SSG를 지원한다. CSR과 SSR을 적절히 섞어 사용할 수 있도록 지원해주기도 한다.
