# 03 다트 비동기 프로그래밍
## 3.1 동기 vs. 비동기 프로그래밍
## 3.2 Future
- 미래에 받아올 값
```
void addNumbers(int number1, int number2) {
    print('계산 시작');
    Future.delayed(Duration(secpmds: 3), () {
        print('$number1 + $number2 = ${number1+number2}');
    });
    print('계산 종료');
}
void main() {
    addNumbers(1,1);
}
```
## 3.3 async와 await
```
Future<void> addNumbers(int number1, int number2) async {
    print('계산 시작');
    await Future.delayed(Duration(secpmds: 3), () {
        print('$number1 + $number2 = ${number1+number2}');
    });
    print('계산 종료');
}
void main() {
    addNumber(1,1)
    addNumber(2,2);
}
void main() async {
    await addNumber(1,1)
    await addNumber(2,2);
}
```
## 3.4 Stream
* Stream 기본 사용법
- Future는 반환값을 한 번만 받아냄
- Stream은 지속적으로 값을 반환 받음
``` 
final controller = StreamController();
final stream = controller.stream;
final streamListener1 = stream.listener( (val) {
    print(val);
});
controller.sink.add(1);
controller.sink.add(2);
```
* 브로드캐스트 스트림
- 스트림은 한 번만 listener() 실행
- 하나의 스트림에 여러번 listener() 함수를 실행하고 싶을 때 사용
``` 
final stream = controller.stream.asBroadcastStream();
```
* 함수로 스트림 반환하기
``` 
Stream<String> calculate(int member) async* {
    for(int i=0; i<number; i++) {
        yield 'i=$i';
        await Future.delayed(Duration(seconds: 1));
    }
}
void playStream() {
    caculator(5).listener({
        print(val);
    });
}
```