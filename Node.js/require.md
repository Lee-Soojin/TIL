# require

require()함수는 export된 module content를 불러온다.

```js
require(id);
```

**id** : module의 이름이나 경로

JSON, local file, module등을 import할때 사용한다.

```js
const myLocalModule = require("./path/myLocalModule");

const jsonData = require("./path/filename.json");

const crypto = require("crypto");
```

Node.js 공식 사이트 문서에 작성되어 있는 예시이다. relative path, json, filename 등을 require 안에 작성하여 호출하고 있다.

require을 이용하여 외부 모듈을 가져올 수 있는 것이다.

예를 들어, text.js를 result.js에서 불러오고 싶을때

```js
// text.js
var hi = function () {
  console.log("hello");
};

module.exports = hi;

//result.js
require("./text.js");
```

이렇게 require로 불러올 수 있다.
이 후 cmd에서 node result.js를 실행하면

```cmd
hello
```

콘솔창에 text.js의 메세지가 표시될 것이다.
