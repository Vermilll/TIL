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
