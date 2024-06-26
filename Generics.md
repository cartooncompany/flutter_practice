## Generics

- 타입을 지정하는 것을 제네릭이라고 한다.

int만을 사용할 목적으로 list를 만들었다고 가정해보자

```dart
List list = [];
```

```dart
list.add(1);
list.add(3);
list.add(5);
```

여기까지는 문제될 요소가 없다. 추후에 이 리스트에 문자열 넣어도 문제가 되지 않는다.

그 이유는 list를 모든 유형을 받을 수 있는 list로 선언했기 때문이다.

이럴 때 제네릭을 사용하는 것이다.

```dart
var list = <int>[];
```

이를 통해 int타입만 지정하게 되면서 다른 유형의 데이터를 list 안에 담으려고 할 때에 오류를 보여주어 개발자가 실수하지 않게 해준다.

이것이 제네릭 Type Safety의 목적을 두고 있다.

Generics 활용의 이점

- 타입 캐스팅에 대한 안정성 보장 → 캐스팅 오류도 방지할 수 있다.
- 효과적인 코딩과 중복 소스 방지
- 형 변환을 해주지 않고도 사용이 가능함