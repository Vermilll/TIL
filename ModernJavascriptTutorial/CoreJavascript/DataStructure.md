## 1. 원시값의 메서드
원시 값은 문자, 숫자, 불린, 심볼, `undefined`, `null`, `bigint` 형으로 7가지가 있다  
객체는 프로퍼티에 함수 등 다양한 값을 저장할 수 있다

#### 원시값을 객체처럼 사용하기
- 원시값을 다루어야 하는 작업이 많은데, 메서드를 사용하면 작업이 수월하다  
- 원시값은 가능한 빠르고 가벼워야 한다  
따라서 원시값이 프로퍼티에 접근하게 하는 원시 래퍼 객체(object wrapper)가 존재한다
```
let str = "hello";
alert (str.toUpperCase()); //HELLO
```
1. str은 원시값으로 원시값의 프로퍼티에 접근하는 순간 해당 원시값과 메서드를 가진 특별한 객체가 만들어진다
2. 메서드가 실행되고 새로운 문자열이 반환된다
3. 특별한 객체는 사라지도 원시값 str만 남는다

## 2. 숫자형
#### 숫자를 입력하는 방법
73억 = `7.3bn`
10억 = `1e9` //1과 9개의 0
0.000001 = `1e-6`

#### 16진수, 8진수, 2진수
```
alert(0xff); //16진수 255
let a = 0b11111111; //2진수 255
let b = 0o377; //8진수 255

alert(255.toString(16)); //ff
```
`toString(base)`는 `base`진법으로 `num`을 변환한 후 문자형으로 반환한다

#### 어림수 구하기
`Math.floor`: 소수점 첫째 자리에서 내림  
`Math.ceil`: 소수점 첫째 자리에서 올림  
`Math.round`: 소수점 첫째 자리에서 반올림  
`Math.turnc`: 소수부를 무시

* 다른 자리 소수점을 구하고 싶을 경우 곱하기와 나누기 10의 배수로 구하거나 `toFixed(n)`을 사용

#### 부정확한 계산
```
alert(0.1 + 0.2 == 0.3) //false, 0.30..04
```
소수는 이진수로 변환되어 메모리 공간에 저장되기 때문에 오류가 발생한다  
`toFixed`(n)`을 사용해 어림수를 만들어 해결할 수 있다

#### isNaN과 isFinite
가장 큰수를 나타내는 `Infinite`와 에러 수를 나타내는 `NaN`는 정상적인 숫자와 구분하기 위한 함수가 존재한다  
- `isNaN(value)`: 인수를 숫자로 변환한 다음 NaN이면 `true`를 반환한다
- `isFinite(value)`: 인수가 `NaN`, `Infinite`가 아닌 일반 숫자인 경우 `true`를 반환한다

#### parseInt와 parseFloat
```
alert(parseInt('100.5px')); //100
alert(parseFloat('12.5em')); //12.5
```
해당 함수는 문자열에서 숫자만 읽고 도중에 오류가 발생하면 수집된 숫자를 반환한다  
읽을 수 있는 숫자가 없을 경우 `NaN`를 반환한다

#### 기타 수학 함수
- `Math.random()`: 0과 1사이의 난수를 반환한다 (1은 제외)
- `Math.max(a, b, c ...)`/`Math.min(...)`: 인수 중 최대/최솟값을 반환한다
- `Math.pow(n, power)`: n을 power번 제곱한 값을 반환한다

## 3. 문자열

#### 따옴표
'작은 따옴표와 "큰 따옴표는 차이가 없지만 백틱은 중간에 `${,,,}`를 통해 표현식을 넣을 수 있다

#### 문자열의 불변성
문자열은 수정할 수 없어서 중간의 글자를 바꾸려고하면 에러가 발생한다  
따라서 새로운 문자열을 만들어야한다
