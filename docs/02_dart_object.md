# 02 다트 객체지향 프로그래밍
## 2.1 객체지향 프로그래밍의 필요성
## 2.2 객체지향 프로그래밍의 시작, 클래스
* 클래스
``` 
class Idol {
    String name = '블랙핑크'; // 멤버 변수
    void sayNname() { // 메서드
        print('나는 ${this.name}입니다');
    }
}
Idol blackPink = Idol();
```
* 생성자
``` 
class Idol {
    final String name;
    Idol(this.name);
    void sayNname() { // 메서드
        print('나는 ${this.name}입니다');
    }
}
Idol blackPink = Idol('blackpink');
```
* 네임드 생성자
``` 
class Idol {
    final String name;
    final int memberCount;
    Idol.fromMap(Map<String, dynamic> map)
        : this.name = map['name'],
        this.memberCount = map['memberCount'];
}
Idol bts = Idol.fromMap({
    'name': 'bts', 'memberCount': 7
});
```
* 프라이빗 변수
- `_`를 활용하여 멤버 변수 선언
``` 
class Idol {
    String _name;
    Idol(this._name)
}
```
* 게터/세터
``` 
class Idol {
    String _name='블랙핑크';
    String get name {
        return this._name;
    }
    set name(String name) {
        this._name = name
    }
}
```
## 2.3 상속
``` 
class Idol {
    final String name;
    final int membersCodunt;
    Idol(this.name, this.memebersCount);
    void sayName() {
        print('저는 ${this.name}입니다')
    }
}

class BoyGroup extends Idol {
    BoyGroup(String name, int membersCount)
        : super(name, membersCount);
}
```
## 2.4 오버라이드
```
class GirlGroup extends Idol {
    GridGroup(super.name, super.membersCount);
    @override
    void sayName() {
        print('여성 그룹 ${this.name}입니다')
    }
}
```
## 2.5 인터페이스
```
class GirlGroup implements Idol {
    final String name;
    final int memberCounts;
    GridGroup(this.name, this.membersCount);
    void sayName() {
        print('여성 그룹 ${this.name}입니다')
    }
}
```
## 2.6 믹스인
- 특정 클래스에 원하는 기능만 골라넣을 수 있는 기능
``` 
mixin IdolSingMixin on Idol {
    void sing() {
        print('${this.name}이 노래를 부릅니다');
    }
}
class BoyGroup extends Idol with IDolSingMixin {
    BoyGroup(super.name, super.mebersCount);
}
```
## 2.7 추상
- 필요한 속성만 정의
- 인스턴스화할 수 없도록 함
``` 
abstract class Idol {
    final String name;
    Idol(this.name);
    void sayName();
}
class GirlGroup implements Idol {
    final String name;
    GirlGroup(this.name);
    void sayNanme() {
        print('여성그룹 ${this.name}입니다');
    }
}
```
## 2.8 제너릭
``` 
class Cache<T> {
    final T data;
    Cache({required this.data});
}
final cache = Cache<List<int>>(data: [1,2,3]);
cache.data.reduce( (value, element) => value +element );
```
## 2.9 스태틱
``` 
class Counter { 
    static int i=0;
    Count() {
        print(i++);
    }
}
Count(); // 1
Count(); // 2
Count(); // 3
```
## 2.10 캐스케이드 연산자
- 인스턴스에서 해당 인스턴스의 속석이나 멤버 함수를 연속해서 사용하는 기능
``` 
Idol blackPink = Idol('블랙핑크', 4)
    ..sayName()
    ..sayMembersCount();
```