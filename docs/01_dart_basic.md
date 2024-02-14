# 01 다트 입문하기
## 1.1 다트 소개
* 특징
- UI 제작 최적화
- 비동기 언어, 이벤트 기반
  - 아이솔레이트를 이용한 동시성 기능 제공
- 널 안정성, 스프레드 기능, 컬렉션 IF문 지원
- 개발할 때 JIT 컴파일러 사용
- 배포할 때 AOT 컴파일러 사용
## 1.2 문법 공부 환경 안내
## 1.3 기초 문법
* 메인 함수
``` 
void main() {

} 
```
* 주석
``` 
void main() {
// 한줄 주석

/* 
여러줄 주석
*/

/// 문서 주석 작성 가능
}
```
* var를 사용한 변수 선언
- `var 변수명 = 값;` 형식으로 선언
- 자동으로 타입 추론
* dynamic을 사용한 변수 선언
- var 타입은 한 번 유츄하면 추론된 타입 고정
- dynamic 키워드를 사용하면 변수의 타입이 고정되지 않음
* final/const를 사용한 변수 선언
- final은 런타임, const는 빌드 타임에 정해짐
``` 
final DateTime now = DateTime.now() // 정상 실행
const DateTime now = DateTime.now() // 에러 발생
```
* 변수 타입
- String, int, double, bool
## 1.4 컬렉션
* List 타입
``` 
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
}
```
- add() 함수
``` 
blackPinkList.add('코드 팩토리')
```
- where() 함수
``` 
final newList = blackPinkList.where(
  (name) => name=='리사'||name=='지수'
);
```
- map() 함수
``` 
final newList = blackPinkList.map(
  (name) => '블랙핑크 $name'
);
```
- reduce() 함수
``` 
final allMembers = blackPinkList.reduce(
  (value, element) => value+','+element
);
```
- fold() 함수
``` 
final memberCount = blackPinkList.fold<int>(
  0,
  (value, element) => value + element.length
);
```
* Map 타입
``` 
Map<String, String> dictionary = {
  'Harry Potter': '해리포터'
};
print(dictionary.keys);
print(dictionary.values);
```
* Set 타입
``` 
Set<String> blackPink = {'로제', '지수', '리사', '제니', '제니'};
```
- 원소 확인
``` 
blackPink.contains('로제');
```
- 리스트 변환
``` 
blackPinkList = blackPink.toList();
```
- 리스트를 Set 타입으로 변환
``` 
Set.from(blackPinkList)
```
* enum 타입
``` 
enum Status {
  approved, pending, rejected
}
```
## 1.5 연산자
* null 관련 연산자
- 타입 뒤에 ?를 명시하면 null 값을 가질 수 있음
``` 
double? number; // 자동으로 null값 지정
number ??= 3; // ?? 사용시 기존 값이 null일 때만 저장
number ??= 4; // number에는 3이 들어가 있으므로 3 유지
```
* 타입 비교 연산자
``` 
int number = 1;
print(number is int); // true
print(number is String); // false
print(number is! int); // false
print(number is! String); // true
```
## 1.6 제어문
* if문
``` 
if(조건1) {
} else if(조건2) {
} else {
}
```
* switch 문
``` 
switch(변수) {
  case 조건1:
    break;
  case 조건2:
    break;
   default:
}
```
* for 문
``` 
for(초깃값; 조건; 증감) {
}
for(변수 in Iterable) {
}
```
* while 문/do..while 문
``` 
while(조건) {
}
do {
} while(조건);
```
## 1.7 함수와 람다
* positional parameter
``` 
int addTowNumbers(int a, int b) {
  return a+b;
}
```
* named parameter
- `required` 키워드 사용
``` 
int addTwoNumbers({
  requried int a,
  required int b
}) {
  return a+b;
}
addTwoNumbers(a:1, b:2);
```
* 기본값 설정
``` 
int addTwoNumbers(int a, [int b=2]) {
  return a+b;
}
addTwoNumbers(1)
```
* positional과 named parameter 섞어 쓰기
- positoinal parameter가 named parameter 보다 먼저 위치해야 함
``` 
int addTwoNumbers(
  int a, {
    required int b,
    int c=4 // required 생략 가능
  }
){
  return a+b+c;
}
addTwoNumbers(1, b:3, c:7);
```
* 익명 함수
```
(매개 변수) {
  함수 바디
}
```
* 람다 함수
``` 
(매개 변수) => 단 하나의 statement
```
* typedef와 함수
- 함수의 시그니처를 정의하는 값
``` 
typedef Operation = void Function(int x, int y);
void add(int x, int y) {
  return x+y;
}
void subtract(int x, int y) {
  return x-y;
}
Operation oper = add;
oper(1,2); // 3
oper = Subtract;
oper(1,2); // -1
```

## 1.8 try...catch
``` 
try {
// 로직 실행
} catch(e) {
// 에러 발생시 에러 처리
}
```