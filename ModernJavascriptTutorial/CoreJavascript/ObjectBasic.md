## 1. 객체
객체는 원시형과 다르게 키와 값을 쌍으로 여러 데이터를 담을 수 있다
```
let user = new Object() ; //객체 생성자
let user = {키:값};            //객체 리터럴
```
#### 리터럴과 프로퍼티 
```
let user = {
name : "john",
age : 30,
};
```
키와 값의 쌍을 하나의 프로퍼티라고 한다  

```
alert(user.name);  //john
alert(user.age);  //30
user.isAdmin = true;
delete user.age;
```
점 표기법으로 키를 지정하여 값을 불러오거나 삭제할 수 있다  
여러 단어로 이름을 만들 때 따옴표로 지정해야 한다 `"like bird":true`  
마지막 프로퍼티 끝도 쉼표로 끝날 수 있다

#### 대괄호 표기법
`user["like bird"] = true`  
`user[key]`  
유효한 식별자가 아닐 때, 변수를 넣고 싶을 때 대괄호 표기법을 사용한다

#### 단축 프로퍼티
```
function makeUser(name, age) {
return {
name,  //name :name 과 같음
age,   //age :age와 같음
};
}

let user = makeUser(john, 30);
alert(user.name); //john
```
기존 변수를 받아와 사용할 때 코드를 줄일 수 있다

#### 프로퍼티 이름의 제약사항
객체 프로퍼티는 `for`, `let`, `return` 같은 예약어를 사용할 수 있다  
단, `__proto__`는 사용할 수 없다

#### `in`연산자로 프로퍼티 존재 찾기
```
"key" in object
```
따옴표로 지정한 키에 해당 프로퍼티가 존재하면 `true`를 반환한다  
`=== undefined`는 비슷하지만 실제로 `undefined`가 값인 경우를 구분할 수 없다  

```
for (let key in object) {
  // key를 이용한 코드 
}
```
`for..in을 이용하여 객체의 모든 키를 순회할 수 있다

#### 객체 정렬 방식
객체의 정수 프로퍼티는 자동으로 정렬되고, 그 외에는 추가한 순서로 정렬된다  
따라서 39과 1이 있으면 무조건 1이 먼저 정렬되지만 +39, +1 로 두면 39를 먼저 둘 수 있다

## 2. 참조에 의한 객체 복사
```
let user = { name: 'john' };
let admin = user;
admin.name = 'peter'; //admin의 참조 값에 의해 데이터 변경
alert(user.name); //peter
```
객체는 변수와 다르게 값 그대로를 할당하는 것이 아닌 값의 데이터 참조 값을 저장한다  
* 객체의 값은 좌표라고 생각하자
* 독립적으로 객체를 복사하고 싶을 땐 빈 객체에 프로퍼티를 순회해 입력하거나 `Object.assign`을 사용한다

## 3. 가비지 컬렉션
```
let  user = {
name: "john" };

user = null;  //name: "john"은 삭제됨
```
가비지 컬렉션은 도달할 수 없는 값으로 가비지 컬렉터에 의해 바로 삭제된다  
외부로 나가는 참조만 가진 값은 도달 가능한 상태에 영향을 주지 않아 삭제된다

## 4. 메서드와 this
```
user = {
sayHi: function() {
alert("hello");
}
};
```
객체의 프로퍼티에 할당된 함수를 메서드라고 한다

#### 메서드 단축 구문
```
uesr = {
sayHi() {
alert("hello");
}
};
```

#### 메서드와 this 
메서드의 내부에 `.`점 앞의 `this`는 해당 객체를 나타낸다  
외부 변수를 사용해 참조할 때에는 원하지 않는 값을 참조할 수 있기 때문에 사용한다  
화살표 함수에서 `this`를 사용하면 외부 변수 this를 가져올 수 있다

## 5. new 연산자와 생성자 함수
#### 생성자 함수
함수 이름은 반드시 대문자로 작성  
반드시 `new`를 붙여 실행
```
function User(name) {
this.name = name;
this.isAdmin = false;
}

let user = new User("보라");

alert(user.name); //보라
alert(user.isAdmin); //false
```
1. 빈 객체를 만들어 `this`에 할당한다  
2. 함수 본문을 실행하여 `this`에 프로퍼티나 메서드를 추가한다
3. `this`를 반환한다  

* `new.target`함수를 사용하면 `new`를 호출했으면 함수를 아니면 `undefined`를 반환한다

#### 생성자와 return문
`return`은
1. 객체에서 사용되면 `this` 대신 함수가 반환된다
2. 원시형에서는 `return`이 무시된다

## 6. 옵셔널 체이닝 '?'
```
let user = {};  //주소 정보가 없는 사용자
alert(user && user.address && user.address.street); //undefined, &&를 사용하지 않으면 에러 발생
```
```
let user = {};
alert(user ?. address ?. street); // undefined
```

`?.`은 앞의 대상이 `undefined`나 `null`이면 평가를 멈추고 `undefined`를 반환한다  
```
let user=null;
let x = 0;

user ?. sayHi(x++); //아무 일도 일어나지 않는다
```
평가 대상에 값이 없는 경우에는 즉시 평가를 멈추기 때문에 오른쪽 동작을 하지 않는다

#### ?.()와 ?.[]
```
let user1 = {
admin(){
alert("관리자 계정");}
};
let user2 = {};

user1.admin?.(); //관리자 계정
user2.admin?.(); //아무 일도 일어나지 않는다
```
`?.()`와 `?.[]`는 객체 존재가 확실할 경우에만 실행하거나 프로퍼티를 읽어 안전하게 객체를 사용할 수 있다

## 7. 심볼형
```
let id1 = Symbol("심볼 이름");
let id2 = Symbol("심볼 이름");

alert(id1 == id2); //false
alert(id1); //error
```
```
let id = Symbol("id");
let user = {
name: "john",
[id]: 123 };
```
객체 프로퍼티의 키는 문자와 심볼만 사용할 수 있는데 심볼은 유일한 식별자이다  
이름표 역할을 하는 심볼 이름이 같아도 영향을 주지 않는다

* 서드 파티에서 가져온 객체를 사용할 때 충돌을 막을 수 있다  
* 키가 심볼인 프로퍼티는 `for..in` 반복문에서 제외 된다

#### 전역 심볼 
```
let id = Symbol.for("id"); //심볼이 존재하지 않으면 새롭게 만든다
let idAgain = Symbol.for("id");

alert(id === idAgain); //true
```
전역 심볼 레지스트리 안에 심볼을 만들면 같은 이름의 심볼에 접근할 때는 동일한 심볼을 반환한다 /

* `Symbol.keyFor`을 사용하면 반대로 전역 심볼의 이름을 얻을 수 있고 `ㅁ.description`은 일반 심볼의 이름을 얻을 수 있다

## 8. 객체를 원시형으로 변환하기
객체의 연산을 하는 등의 특정 행동은 객체가 원시형으로의 자동 형변환이 일어난다
#### ToPrimitive
특수 객체 메서드를 사용하면 원하는 형으로의 변환을 할 수 있는데 'hint'값이 구분 기준이 된다
`"string"` : 문자열을 기대하는 연산에서는 hint가 `string`이 된다
`"number"` : 수학 연산에서는 hint가 `number`가 된다
`"defalt"` : 기대하는 자료형이 확실하지 않을 때에는 hint가 `defalt`가 된다
* bollead hint값은 없다

#### Symbol.toPrimitive
```
obj[Symbol.toPrimitive] = function(hint) {
 // 반드시 원시 값을 반환해야 한다
 };
 ```
 해당 메서드를 통해 목표로 하는 자료형을 명명한다
 
 #### toString과 valueOf
 `Symbol.toPrimitive`가 없으면 자바스크립트는 `toString`과 `valueOf`를 호출한다  
 hint가 string일 경우 `toString` -> `valueOf`순으로 호출하고 그 외에는 반대 순서로 호출한다
