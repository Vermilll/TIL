## 1. Hello,world!
#### <script> 태그
  `<script>` 태그 사이에 자바스크립트 코드 삽입 가능하다
  ```
  <script>
  alert("Hello,world!");
  </script>
  ```

#### 외부 스크립트
src 속성(attribute)을 사용하여 HTML에 삽입 가능하다
```
<scritp src="/path/to/script.js">
</script>
```    
  
*scr 속성이 있을 경우 내부의 코드는 무시된다

## 2. 코드 구조
#### 문(statement)
어떤 작업을 수행하는 문법 구조와 명령어로 세미콜론;으로 구분한다  
  
*자바스크립트는 줄바꿈을 암시적 세미콜론으로 인식하기도 한다

#### 주석
한 줄의 주석은 //로 표현하고 여러 줄의 주석은 /*로 시작하여 */로 끝난다  
  
*단축키 ctrl+/로 한 줄 주석이나 ctrl+shift+/로 여러 줄을 주석으로 만들 수 있다

## 3. 엄격 모드
--생략--

## 4. 변수와 상수
#### 변수
변수는 이름이 붙은 저장소로 `let`을 통해 선언할 수 있다
```
let message;
message = "Hello";
alert(message);
```

#### 변수 명명 규칙
1. 변수에는 오직 문자와 `$`와 `_`만 들어갈 수 있다
2. 첫 글자는 숫자가 될 수 없다

#### 상수
변화하지 않는 상수를 설정할 때에는 `let`대신 `const`를 사용한다  
값이 변하지 않을 것을 확신하면 값이 변경되는 것을 방지하고  
다른 개발자에게 상수라는 것을 알리기 위한 용도로 사용한다 
  
*기억하기 힘든 값의 별칭으로 사용한다  
*대문자와 밑줄로 만드는 것이 관습이다

#### 바람직한 변수명
사람이 읽을 수 있는 이름을 사용하는 것이 좋다  
간결하고 명확해야 한다  
최대한 서술적이고 간결해야 한다

## 5. 자료형
#### 숫자형
일반적인 숫자 말고도 `infinity`, `-infinity`, `NaN` 등이 포함된다

#### 문자형
따옴표로 사용한다
```
let name="john";
alert("hello, ${name}!"); //hello,john!
alert("result ${1+2}");   //result 3
```
`${}`를 사용해 문자형 안에 표현식을 넣을 수 있다

#### 불린형
`true`와 `false` 두 가지 값만 있다

#### null과 undefined
`null`은 비어있거나 알수없는 값을, `undefined`는 값이 할당되지 않은 상태를 나타낸다

#### typeof
`typeof` 연산자는 해당 인수의 자료형을 반환한다

## 6. 기본 브라우저 상호작용
#### alert
`alert("check")` 사용자가 확인을 누를 때 까지 메시지를 보여주는 창을 띄운다

#### prompt
```
result = prompt(title, [defalt])
```
`title` 사용자에게 보여줄 문자열  
`defalt` 입력 공간의 초깃값  
사용자가 입력한 값을 반환하고 입력을 취소했을 경우 `null`을 반환한다   
  
*대괄호`[]`는 필수가 아닌 선택값을 의미한다

#### confirm
`result=confirm(question)`  
`confirm`은 매개변수로 받은 question과 확인, 취소 버튼이 있는 모달 창을 보여준다  
확인은 `true`, 취소는 `false`를 반환한다

## 7. 형 변환
#### 문자형으로 변환
`alert("value")`는 매개 변수를 문자형으로 받기 때문에 자동으로 value는 문자형으로 변환된다  
`String(value)` 함수로 값을 문자열로 변환할 수 있다

#### 숫자형으로 변환
숫자 이외의 값을 숫자형으로 변환하려고 하면 결과는 NaN이 된다
```
alert(Number("  123  ")); //123
alert(Number("123z"));    //NaN
alert(Number(true));      //1
alert(Number(false));     //0
```

#### boolean형으로 변환
`boolean(value)`는 0, null, NaN 등 비어있다고 판단되는 값을 false로 하고  
그 외의 값을 true로 한다
``` 
alert(boolean("hello")); // true 
```

## 8. 기본 연산자와 수학
피연산자 : 연산의 대상이 되는 숫자  
단항 : 피연산자를 하나만 받는 연산자  
이항 : 피연사자를 두 개 받는 연산자

#### 수학
덧셈 연산자 `+`   
뺄셈 연산자 `-`  
곱셈 연산자 `*`  
나눗셈 연산자 `/`  
나머지 연산자 `%`  
거듭제곱 연산자 `**`

#### 단 연산자 +
`+`가 단항 연산자로 사용되면 숫자에는 영향을 주지 않고, 문자열을 숫자열로 바꾼다
```
let apple = '2';
let orange = '3';

alert(+apple + +orange); //5
```

#### 복합 할당 연산자
할당 연산자 `=` 앞에 다른 연산자를 입력하면 짧은 문법으로 연산을 수행할 수 있다
```
let n=2;
n *= 3 + 5;
alert(n);  //16
```

#### 증가'감소 연산자
`++`와 `--`는 변수의 앞뒤에 배치해 변수를 1증가시키거나 감소시킬 수 있다  
피연산자의 앞인지 뒤인지에 따라서 반환과 연산의 순서를 정할 수 있다

#### 비트 연산자
비트 연산자는 인수를 32비트 정수로 변환하여 연산한다  
비트 AND (`&`)  
비트 OR (`|`)  
비트 XOR (`^`)  
비트 NOT (`~`)  
왼쪽 shift (`<<`)  
오른쪽 shift (`>>`)  

## 9. 비교 연산자        
비교 연산자는 불린형(`true`, `false`)을 반환한다

#### 문자열 비교
동등 연산자(`==`)는 사전 뒤쪽의 문자가 사전 앞쪽의 문자보다 크다고 비교된다
```
alert('Z'<'A'); //true
alert('Be' < 'Bee'); //true
```
  
*일치 연산자(`===`)는 타입까지 비교한다

#### 다른 형을 가진 값 비교
비교 대상이 서로 다른 타입을 가지고 있다면 이 값들을 숫자로 바꾸어 비교한다
`alert('2' > 1); //true`
`true`는 1, `false`는 0으로 변환된다

## 10. if와 ?를 사용한 조건 처리
  #### if문
  ```
  if (year == 2015){
  alert("정답입니다");}
  ```
  if문은 괄호안의 내용이 true일 때 코드가 실행된다  
  
  *숫자`0`, 빈문자`"  "`, `null`, `undefined`, `NaN`은 불린형으로 변환시 `false`가 되고 이외의 값은 `true`가 된다
  
  #### else절
  if문에는 else를 붙여 조건이 `false`일 때 실행할 수 있다  
  else if를 붙여 여러 조건을 처리할 수 있다
  
  #### 조건부 연산자 ?
  `let result = condition ? value1 : value2;`  
  condition이 truthy라면 value1이 그렇지 않으면 value2가 반환된다
  ```
  let message = (age <3) ? '아기야, 안녕' :
  (age < 18) ? '안녕' :
  '환영합니다';
  
  alert(message);
  ```
## 11. 논리 연산자
  #### ||(OR)
  ```
  result = a || b;
  ```
or 연산자는 피연산자 둘 중 하나라도 `true`일 경우 `true`를 반환한다  
  
  ```
  result = a || b || c
  ```
  or 연산자아 피연산자가 여러개일 경우  
  왼쪽부터 불린형으로 변환하여 `true`인 값을 인식했을 경우 해당 피연산자를 반환한다
  
  #### &&(AND)
  ```
  result = a && b
  ```
  and연산자는 피연산자가 둘 다 `true`일 경우에 `true`를 반환한다  
  
  and연산자와 피연산자가 여러개일 경우 왼쪽부터`falsy`값을 인식하여 피인식자를 반환한다
  
  #### !(NOT)
  !연산자는 피연산자를 불린형으로 변경하고 반대되는 값을 반환한다  
  !를 두 번 사용하면 값을 불린형으로 변환한다
  
  ## 12. nullish 병합 연산자
  nullish 병합 연산자를 사용한 평가 `a ?? b`에서  
  a가 null이나 undefined가 아니면 a  
  그외의 경우 b를 반환한다  
  
  ```
  height = height ?? 100;
  ```
  변수에 기본값을 할당하는데에 사용할 수 있다
  
  
## 13. While과 for 반복문

#### while 반복문
```
while(condition) {
//코드}
```
조건이 truthy이면 코드를 실행한다  
  
*`while(true)`를 사용하여 무한 반복문을 만들 수 있다  
*`while(i)`는 i `!= 0`를 의미한다

#### do-while 반복문
```
do{  //코드
}while(condition) 
```
코드가 먼저 실행되고 조건으로 넘어간다  
코드를 한 번이라도 실행시키고 싶을 경우 사용한다

#### for 반복문
```
for(begin, condition, step){
//본문}
```
begin은 반복문 최초 실행 시 실행되고, step은 body가 실행될 때 마다 실행된다

*반복문 등의 안에서 선언된 인라인 변수는 해당 문안에서만 접근할 수 있다

#### break와 continue
`break`함수 사용 시 반복문을 중단, `continue`함수 사용 시 본문을 중단시키고 다음 반복으로 넘어간다    
  
*`continue`는 중첩을 줄여 코드 가독성에 도움을 준다  
*삼항연산자`?` 오른쪽에는 `continue`나 `break`를 놓으면 안된다

#### 중첩 반복문에서 나오기
```
labelname: for() {}
```
레이블은 반복문 앞에 사용되면 중첩된 반복문 안에서 `break labelname`을 사용하여 한 번에 빠져나올 수 있다

  ## 14. switch문
  복수의 if문은 switch문으로 사용할 수 있다
  ##### 문법
  ```
  switch(x) {
  case 'value1' :
  ...
  [break]
  
  case 'value2' :
  ...
  [break]
  
  defalt:
  ...
  [break]}
  ```
  변수 x의 값과 value가 일치하면 코드를 실행한다  
  `break`문이 없으면 일치하는 case 다음의 코드도 전부 실행된다 
  일치하는 value의 case가 없다면 defalt의 코드가 실행된다  
  
  *x와 value가 같은 형이어야 한다
  
  ## 15. 함수
  #### 함수 선언
  ```
  function name(parameters){
  함수 본문 }
  ```
  함수 내에서 선언한 지역 변수(local variable)은 함수 안에서만 접근할 수 있다  
  함수 내부에서 외부 변수에 접근할 수 있다
  
  #### 기본값
  매개 변수에 값을 주지 않으면 `undefined`가 된다  
  매개 변수 오른쪽에 `=기본값`을 입력하면 매개 변수가 입력되지 않았을 경우 입력한 값이 적용된다
  ```
  function showMessage(from, text = 'no given message') {
  alert(from + ":" + text); }
  ```
  혹은
  ```
  function showMessage(text){
  if text == undefined {
  text = '빈 문자열'; }
  ```
  
  #### 반환 값
  코드 실행 중 `return`함수를 만나면 함수는 종료되고 해당 값을 반환한다
  ```
  function sum(a, b) {
  return a + b; }
  ```
  
  #### 함수 이름 짓기
  함수는 보통 동작을 나타낸다  
  `show` 무언가를 보여주는 함수  
  `get` 값을 반환하는 함수  
  `calc` 값을 계산하는 함수  
  `create` 무언가를 생성하는 함수  
  `check` 무언가를 확인하고 불린값을 반환하는 함수  
  *함수는 이름에 언급된 동작 하나만 실행해야 한다
  
  ## 16. 함수 표현식
  ```
  let sayHi = fucntion() {
  alert("hello"); };
  ```
  함수는 위와 같은 함수 표현식으로 나타낼 수 있다  
  함수`sayHi`도 값이기 때문에 다른 값처럼 복사하거나 사용할 수 있다
  
  #### 콜백 함수
  ```
  function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
  }
  
  function showOkay() {
  alert("동의하셨습니다");
  }
  
  function showCancle() {
  alert("취소하셨습니다");
  }
  
  ask("동의하십니까?", showOkay, showCancle);
  ```
  `showOkay`와 `showCancle`을 함수를 다른 함수의 인수로 전달하고 나중에 호출하는 콜백함수라고 한다
  
  ```
  ask(
  "동의하십니까?",
  function() {alert ("동의하셨습니다");},
  function() {alert ("취소하셨습니다");} );
  ```
  이름없이 선언한 함수를 익명 함수라고 한다
  
  #### 함수 표현식과 함수 선언문
  함수 표현식은 실제 실행 흐름이 함수 선언문에 도달했을 때 함수를 생성한다  
  함수 선언문은 스크립트가 어디에 있는지 상관없이 사용할 수 있다
  
  ## 17. 화살표 함수 기본
  ```
  let func = (arg1, arg2, .. argN) => expression
  ```
  인자 arg1~argN을 받는 함수 func를 생성하고, 함수 func는 expression을 평가하고 반환한다  
  중괄호와 함께 여러 줄로 작성했다면 `return`지시자를 사용해 반환해야 한다
  
  ## 18. 기본 문법 요약
  https://ko.javascript.info/javascript-specials
