# 정규표현식(RegExp)

정규식, Regular Expression

---

## 역할

- 문자 검색(search)
- 문자 대체(replace)
- 문자 추출(extract)



## 테스트 사이트

https://regexr.com/




## 정규식 생성

```js
//생성자
new RegExp('표현', '검색 옵션(플래그)')
new RegExp('[a-z]', 'gi') //g: global, 일치하는 모든 내용 검색 / i: 대소문자구분X

//리터럴
/표현/옵션
/[a-z]/gi
```


## 예제 문자
```js
const str =` 
010-1234-5678
abc@gmail.com
https://www.omdbapi.com/?apikey=7035c60c&s=frozen'
The quick brown fox jumps over the lazy dog.
abbcccdddd
`
```


## 메소드

메소드 | 문법 | 설명
--|--|--
test | `정규식.test(문자열)` | 일치 여부(Boolean) 반환
match | `문자열.match(정규식)` | 일치하는 문자의 배열(Array) 반환
replace | `문자열.replace(정규식, 대체문자)` | 일치하는 문자를 대체해 반환 (원본데이터를 손상시키지는 않음)


## 플래그

플래그 | 설명
-- | --
g | 일치하는 모든 문자(global)
i | 영어 대소문자 구분 없이 일치(ignore case)
m | 여러 줄 일치 (multi line)


const regexp = /the/gi
console.log(str.match(regexp))
또는 
console.log(str.match(/the/gi))
형태로 사용

_g를 붙이지 않을 때는 일치하는 문자 중 가장 먼저 찾아진 문자 한개만 반환하고, 그 위치의 인덱스값이 같이 나온다.

m : 하나의 문자데이터는 시작과 끝이 한개씩만 존재하지만,
문자데이터 내부에서 줄바꿈이 되어있다면, 줄 각각에서 시작과 끝을 임의지정하겠다는 의미
_줄 : 줄바꿈과 관계 없이 문자열의 시작부터 끝을 의미_

## 패턴(표현)

패턴 | 설명
-- | --
^ab | 줄(Line) 시작에 있는 ab와 일치시킴
ab$ | 줄(Line) 끝에 있는 ab와 일치시킴
. | 임의의 한 문자와 일치시킴
a&verbar;b | a또는 b와 일치시킴
ab? | b가 없거나 b와 일치
{3} | 3개 연속 일치
{3,} | 3개 이상 연속 일치
{3,5} | 3개 이상 5개 이하(3~5개) 연속 일치
\w{3,5} | 숫자와 문자가 포함된 3개 이상 5개 이하와 일치
[abc] | a 또는 b 또는 c
[a-z] | a부터 z 사이의 문자 구간에 일치(영어 소문자)
[A-Z] | A부터 Z 사이의 문자 구간에 일치(영어 대문자)
[0-9] | 0부터 9까지의 문자 구간에 일치
[가-힣] | 가부터 힣 사이의 문자 구간에 일치(한글)
\w | 63개 문자(Word, 대소영문52개 + 숫자 10개 + _)에 일치
\b | 63개 문자에 일치하지 않는 문자 경계(Boundary) - 글자와 글자 사이의 구분(특수기호, 공백 등)
\d | 숫자(Digit)에 일치
\s | 공백(Space, Tab, 줄바꿈 등)에 일치
(?=) | 앞쪽 일치(Lookahead)
(?<=) | 뒤쪽 일치(Lookbehind)