## 1. Hello,world!
### <script> 태그
  `<script>` 태그 사이에 자바스크립트 코드 삽입 가능하다
```
  <script>
    alert("Hello,world!");
  </script>
  ```
  
  ### 외부 스크립트
  src 속성(attribute)을 사용하여 HTML에 삽입 가능하다
  ```
  <scritp src="/path/to/script.js">
  </script>
  ```  
  *scr 속성이 있을 경우 내부의 코드는 무시된다

  ## 2. 코드 구조
  ### 문(statement)
  어떤 작업을 수행하는 문법 구조와 명령어로 세미콜론;으로 구분한다
  *자바스크립트는 줄바꿈을 암시적 세미콜론으로 인식하기도 한다
  
  ### 주석
  한 줄의 주석은 //로 표현하고 여러 줄의 주석은 /*로 시작하여 */로 끝난다
  *단축키 ctrl+/로 한 줄 주석이나 ctrl+shift+/로 여러 줄을 주석으로 만들 수 있다
  
  ## 3. 엄격 모드
  --생략--
  
  ## 4. 변수와 상수
  ### 변수
  변수는 이름이 붙은 저장소로 `let`을 통해 선언할 수 있다
  ```
  let message;
  message = "Hello";
  alert(message);
  ```
  
  ### 변수 명명 규칙
  1. 변수에는 오직 문자와 `$`와 `_`만 들어갈 수 있다
  2. 첫 글자는 숫자가 될 수 없다
  
  ### 상수
  변화하지 않는 상수를 설정할 때에는 `let`대신 `const`를 사용한다  
  값이 변하지 않을 것을 확신하면 값이 변경되는 것을 방지하고  
  다른 개발자에게 상수라는 것을 알리기 위한 용도로 사용한다
  *기억하기 힘든 값의 별칭으로 사용한다  
  *대문자와 밑줄로 만드는 것이 관습이다
  
  ### 바람직한 변수명
  사람이 읽을 수 있는 이름을 사용하는 것이 좋다  
  간결하고 명확해야 한다  
  최대한 서술적이고 간결해야 한다
  
  ## 5. 자료형
  ### 숫자형
  일반적인 숫자 말고도 `infinity`, `-infinity`, `NaN` 등이 포함된다
  
  ### 문자형
  따옴표로 사용한다
  ```
  let name="john";
  alert("hello, ${name}!"); //hello,john!
  alert("result ${1+2}");   //result 3
  ```
  `${}`를 사용해 문자형 안에 표현식을 넣을 수 있다
  
  ### 불린형
  `true`와 `false` 두 가지 값만 있다
  
  ### null과 undefined
  `null`은 비어있거나 알수없는 값을, `undefined`는 값이 할당되지 않은 상태를 나타낸다
  
  ### typeof
  `typeof` 연산자는 해당 인수의 자료형을 반환한다
  
  ## 6. 기본 브라우저 상호작용
  ### alert
  `alert("check")` 사용자가 확인을 누를 때 까지 메시지를 보여주는 창을 띄운다
  
  ### prompt
  ```
  result = prompt(title, [defalt])
  ```
  `title` 사용자에게 보여줄 문자열  
  `defalt` 입력 공간의 초깃값  
  사용자가 입력한 값을 반환하고 입력을 취소했을 경우 `null`을 반환한다   
  *대괄호`[]`는 필수가 아닌 선택값을 의미한다
  
  ### confirm
  `result=confirm(question)`  
  `confirm`은 매개변수로 받은 question과 확인, 취소 버튼이 있는 모달 창을 보여준다  
  확인은 `true`, 취소는 `false`를 반환한다
  
  ## 7. 형 변환
  ### 문자형으로 변환
  `alert("value")`는 매개 변수를 문자형으로 받기 때문에 자동으로 value는 문자형으로 변환된다  
  `String(value)` 함수로 값을 문자열로 변환할 수 있다
  
  ### 숫자형으로 변환
  숫자 이외의 값을 숫자형으로 변환하려고 하면 결과는 NaN이 된다
  ```
  alert(Number("  123  ")); //123
  alert(Number("123z"));    //NaN
  alert(Number(true));      //1
  alert(Number(false));     //0
  ```
  
  ### boolean형으로 변환
  `boolean(value)`는 0, null, NaN 등 비어있다고 판단되는 값을 false로 하고  
  그 외의 값을 true로 한다
  ``` 
  alert(boolean("hello")); // true 
  ```
  
  ## 13. While과 for 반복문
  
  ### while 반복문
 ```
  while(condition) {
  //코드}
 ```
  조건이 truthy이면 코드를 실행한다  
  *`while(true)`를 사용하여 무한 반복문을 만들 수 있다  
  *`while(i)`는 i `!= 0`를 의미한다
  
  ### do-while 반복문
  ```
  do{  //코드
  }while(condition) 
  ```
  코드가 먼저 실행되고 조건으로 넘어간다  
  코드를 한 번이라도 실행시키고 싶을 경우 사용한다
  
  ### for 반복문
  ```
  for(begin, condition, step){
  //본문}
  ```
  begin은 반복문 최초 실행 시 실행되고, step은 body가 실행될 때 마다 실행된다
  
  *반복문 등의 안에서 선언된 인라인 변수는 해당 문안에서만 접근할 수 있다
  
  ### break와 continue
  `break`함수 사용 시 반복문을 중단, `continue`함수 사용 시 본문을 중단시키고 다음 반복으로 넘어간다    
  *`continue`는 중첩을 줄여 코드 가독성에 도움을 준다  
  *삼항연산자`?` 오른쪽에는 `continue`나 `break`를 놓으면 안된다
  
  ### 중첩 반복문에서 나오기
  ```
  labelname: for() {}
  ```
  레이블은 반복문 앞에 사용되면 중첩된 반복문 안에서 `break labelname`을 사용하여 한 번에 빠져나올 수 있다
