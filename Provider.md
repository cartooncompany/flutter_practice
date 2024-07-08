## Provider란?

---

Flutter는 상태를 가지지 않는 stateless 위젯과 stateful 위젯으로 나뉜다.

여기서 서로 다른 위젯에서 동일한 상태(데이터)가 필요한 경우 어떻게 해야할까요?

Provider는 이를 해결하기 위해 등장하였으며 동일한 상태(데이터)를 전역적으로 다른 위젯들과 공유할 수 있게 해줍니다.

Provider를 사용하기 위해서는 위젯 트리와 상관없이 상태(데이터)를 저장할 클래스를 생성하고, 해당 상태를 공유하는 공통 부모 위젯에 Provider를 제공하고 상태를 사용하는 곳에는 Provider의 데이터를 읽어서 사용하게 된다.

## Provider 패키지 설치

---

Flutter에서 전역 상태 및 위젯 간의 상태 공유를 위해 아래 명령어를 실행하여 provider 패키지를 설치한다.

```dart
flutter pub add provider
```

## 사용법

---

먼저 provider를 생성해 봅시다.

```dart
import 'package:flutter/material.dart';

class Counts with ChangeNotifier {
  int _count = 0;
  int get count => _count;

  void add(){
    _count++;
    notifyListeners();
  }

  void remove(){
    _count--;
    notifyListeners();
  }
}
```

Provider를 사용하기 위해서는 ChangeNotifier을 사용해야 합니다.

그리고 앱 내에서 공유할 상태 변수를 선언합니다. 또한 해당 변수를 외부에서 접근할 수 있도록 getter도 생성합니다.

위 코드에서는 값을 증가시키는 add, 값을 감소시키는 remove함수를 생성하였습니다.

여기서 중요한 점은 변수를 수정하였다면, notifyListeners()를 실행시켜 데이터가 갱신되었음을 통보한다.

*notifyListeners()를 사용하지 않으면 변화한 것을 인식하지 못합니다.

## Main

---

```dart
import 'package:flutter/material.dart';
import 'package:prcprovider/Counter.dart';
import 'buttons.dart';
import 'package:prcprovider/provider_counts.dart';
import 'package:provider/provider.dart';

void main(){
  runApp(
      ChangeNotifierProvider(
        create: (_) => Counts(),
        child: MyApp(),
      ),
  );
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Home(),
    );
  }
}

class Home extends StatefulWidget {
  const Home({super.key});

  @override
  State<Home> createState() => _HomeState();
}

class _HomeState extends State<Home> {
  @override
  Widget build(BuildContext context) {
    return const Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Counter(),
            Buttons(),
          ],
        ),
      ),
    );
  }
}
```

이 예제 코드에서는 ChangeNotifierProvider를 사용하여 앱 전체에 Provider를 제공할 수 있도록 하였습니다.

이제 아래 코드에서 Counter와 Buttons을 구현하도록 하겠습니다.

## Counter

---

```dart
import 'package:flutter/material.dart';
import 'package:prcprovider/provider_counts.dart';
import 'package:provider/provider.dart';

class Counter extends StatelessWidget {
  const Counter({super.key});

  @override
  Widget build(BuildContext context) {
    print('Counter');

    return Text(
      context.watch<Counts>().count.toString(),
      style: const TextStyle(fontSize: 20),
    );
  }
}
```

이는 화면에 text를 출력하는 단순한 위젯입니다. 이때, context.watch<Counts>().count를 사용하여 우리가 만든 Provider의 count의 값이 변경되는지를 감시하, 변경이 실패하면 화면에 변경된 값을 표시하도록 하였습니다.

## Buttons

---

```dart
import 'package:flutter/material.dart';
import 'package:prcprovider/provider_counts.dart';
import 'package:provider/provider.dart';

class Buttons extends StatelessWidget {
  const Buttons({super.key});

  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        ElevatedButton(onPressed: (){
          context.read<Counts>().add();
        }, child: const Icon(Icons.add)),
        const SizedBox(
          width: 40,
        ),
        ElevatedButton(onPressed: (){
          context.read<Counts>().remove();
        }, child: const Icon(Icons.remove)),
      ],
    );
  }
}

```

이 위젯은 Counter와 다르게 Provider의 count값을 변경하기 위해서 context.read<Counts>()를 사용하여 add와 remove를 호출하였습니다.

## watch, read, select

---

Provider에서는 watch, read, select의 기능을 제공합니다

- watch: 해당 위젯이 변경 값을 감시합니다.
- read: 해당 위젯은 상태 값을 읽습니다. 하지만 변경을 감시하지 않습니다.
- select: 해당 위젯은 상태값의 특정 부분만 감시합니다.