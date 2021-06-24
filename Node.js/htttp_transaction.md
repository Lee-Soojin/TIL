# Node.js 의 HTTP 처리 과정

**참고** : <https://nodejs.org/ko/docs/guides/anatomy-of-an-http-transaction/>

## • 서버 생성

```js
const http = require("http");

const server = http.createServer((request, response) => {
  // 여기서 작업이 진행됩니다!
});
```

서버로 오는 http 요청마다 createServer 안의 함수가 한번씩 실행된다.

```js
const server = http.createServer();
server.on("request", (request, response) => {
  // 여기서 작업이 진행됩니다!
});
```

HTTP 요청이 서버에 오면 node가 transaction을 다루려고 **request, response**객체를 전달하며 **요청 핸들러 함수**를 호출한다.

요청을 실제로 처리하려면 **listen** 메서드가 server 객체에서 호출되어야 한다. 서버가 사용하고자 하는 포트 번호를 listen에 전달하기만 하면 된다.

## • 메서드, URL, headers

요청 시 메서드와 URL을 확인 후 관련된 적절한 작업을 실행하려고 할 것이다.

```js
const { method, url } = request;
```

method는 항상 일반적인 http 메서드/동사가 될 것이다. url은 전체 URL에서 서버, 프로토콜, 포트를 제외한 것이다.

예를 들면

```
http://locaclhost:3000/main?id=blah&page=10
```

위의 URL에서 `main?id=blah&page=10` 부분이 url에 들어가게 되는 것이다.

```js
const { headers } = request;
const userAgent = headers["user-agent"];
```

request에 headers라는 전용 객체가 있다. 모든 헤더는 소문자로만 표현이 된다.

## • 요청 바디

POST , PUT 요청을 받을 때 애플리케이션에서 요청 바디는 중요하다. 요청 헤더에 접근하는 것보다 바디 데이터를 받는 것은 더 어렵다.

```js
let body = [];
request
  .on("data", (chunk) => {
    body.push(chunk);
  })
  .on("end", () => {
    body = Buffer.concat(body).toString();
    // 여기서 `body`에 전체 요청 바디가 문자열로 담겨있습니다.
  });
```

```
💡 중간 설명

    request('data',callback)
```

request에 data가 있을 경우 처리된다.

```
    request('end', callback)
```

data처리가 다 끝났음을 알린다.

스트림의 'data'와 'end' 이벤트에 이벤트 리스너를 등록해서 데이터를 얻는 것이다.

## • 오류

request 스트림의 오류가 발생하면 스트림에서 'error' event가 발생하면서 오류를 전달한다. 이벤트 리스너가 등록되어 있지 않다면 프로그램이 종료될 수 있다. 따라서 요청 스트림에 'error'리스너를 추가해야 한다.

```js
request.on("error", (err) => {
  // 여기서 `stderr`에 오류 메시지와 스택 트레이스를 출력합니다.
  console.error(err.stack);
});
```

```js
const http = require("http");

http
  .createServer((request, response) => {
    const { headers, method, url } = request;
    let body = [];
    request
      .on("error", (err) => {
        console.error(err);
      })
      .on("data", (chunk) => {
        body.push(chunk);
      })
      .on("end", () => {
        body = Buffer.concat(body).toString();
        // 여기서 헤더, 메서드, url, 바디를 가지게 되었고
        // 이 요청에 응답하는 데 필요한 어떤 일이라도 할 수 있게 되었습니다.
      });
  })
  .listen(8080); // 이 서버를 활성화하고 8080 포트로 받습니다.
```

위를 실행하면 요청을 받을 수 있다. response 객체는 건들이지 않았으므로 아직 응답은 하지 않는다.

## • HTTP status code

default status code 는 항상 200이다.

```js
response.statusCode = 400;
```

상태 코드를 변경하려면 statusCode 프로퍼티를 설정해야 한다.

## • 응답 헤더 설정

```js
response.setHeader("Content-Type", "application/json");
response.setHeader("X-Powered-By", "bacon");
```

setHeader 메서드로 헤더를 설정한다.

## • writeHead

writeHead를 이용하면 응답 스트림에 헤더를 작성할 수 있다. 이 메서드는 스트림에 status code, header를 작성한다.

```js
response.writeHead(200, {
  "Content-Type": "application/json",
  "X-Powered-By": "bacon",
});
```

## • 응답 바디 전송

```js
response.write("<html>");
response.write("<body>");
response.write("<h1>Hello, World!</h1>");
response.write("</body>");
response.write("</html>");
response.end();
```

위의 예제는 end를 이용해 간단하게 작성할 수 있다.

```js
response.end("<html><body><h1>Hello, World!</h1></body></html>");
```

## • 오류

response 스트림의 'error'도 request 스트림의 오류와 동일하다.

## • response까지 추가한 예제

```js
const http = require("http");

http
  .createServer((request, response) => {
    const { headers, method, url } = request;
    let body = [];
    request
      .on("error", (err) => {
        console.error(err);
      })
      .on("data", (chunk) => {
        body.push(chunk);
      })
      .on("end", () => {
        body = Buffer.concat(body).toString();
        // 여기서부터 새로운 부분입니다.

        response.on("error", (err) => {
          console.error(err);
        });

        response.statusCode = 200;
        response.setHeader("Content-Type", "application/json");
        // 주의: 위 두 줄은 다음 한 줄로 대체할 수도 있습니다.
        // response.writeHead(200, {'Content-Type': 'application/json'})

        const responseBody = { headers, method, url, body };

        response.write(JSON.stringify(responseBody));
        response.end();
        // 주의: 위 두 줄은 다음 한 줄로 대체할 수도 있습니다.
        // response.end(JSON.stringify(responseBody))

        // 새로운 부분이 끝났습니다.
      });
  })
  .listen(8080);
```

💡 **request 객체는 읽기 가능 스트림이고 response 객체는 쓰기 가능 스트림인 점이 중요하다.**
