# 변수선언
var
변수를 선언. 추가로 동시에 값을 초기화.

let
블록 스코프 지역 변수를 선언. 추가로 동시에 값을 초기화.

const
블록 스코프 읽기 전용 상수를 선언.

자바스크립트에서 변수 선언은 선언 → 초기화 단계를 거쳐 수행된다.

선언 단계: 변수명을 등록하여 자바스크립트 엔진에 변수의 존재를 알린다.
초기화 단계: 값을 저장하기 위한 메모리 공간을 확보하고 암묵적으로 undefined를 할당해 초기화한다.


### var:변수 재선언 가능
```javascript
var one=1;
console.log(one); //변수선언

var one=2;
console.log(one); //변수재선언

```


### let: 변수 재선언 불가능, 재할당 가능
```javascript
let one=1;
console.log(one); // 변수선언

one=2;
console.log(one); // 변수 재할당

let one=3;
console.log(one); // Uncaught SyntaxError: Identifier 'variable' has already been declaredㅣ

```

### const: 변수 재선언 불가능, 재할당 불가능
```javascript
const one=1;
console.log(one); // 변수선언

const=2;
console.log(one); // 변수 재할당 error

let one=3;
console.log(one); // 변수 재선언 error

```
const는 let과 다르게 반드시 선언과 초기화가 동시에 진행되어야 한다.
```javascript
let one;
one='1';

const name; // output: Uncaught SyntaxError: Missing initializer in const declaration
const name = 'seo'
```
원시값의 대한 재할당은 불가능하지만 객체는 가능하다.


```javascript
const name = 'seo'
name = 'kim' // output: Uncaught TypeError: Assignment to constant variable.

// 객체의 재할당
const name = {
  eng: 'kim',
}
name.eng = 'seo'

console.log(name) // output: { eng: "seo" }
```

### 블록 레벨 스코프

##### var : 함수 레벨 스코프 (function-level scope)
```javascript
if (true) {
  var x = 5;
}
console.log(x); // 5
```
수 내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없음. 
즉, 함수 내부에서 선언한 변수는 지역 변수이고 함수 외부에서 선언한 변수는 모두 전역 변수로 취급됨.


#####  let, const : 블록 레벨 스코프 (block-level scope)
```javascript
if (true) {
  let y = 5;
}
console.log(y); // ReferenceError: y is not defined
```
함수, if문, for문, while문, try/catch문 등의 모든 코드 블록 ({...}) 내부에서 선언된 변수는 코드 블록 내에서만 유효하며 코드 블록 외부에서는 참조할 수 없음.
즉, 코드 블록 내부에서 선언한 변수는 지역 변수로 취급됨.
