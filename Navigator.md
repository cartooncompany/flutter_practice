## Navigator

- Navigator는 다양한 유형의 정보를 표시하기 위해 앱에는 여러 화면이 있는데 이때 화면 전환 역할을 돕는데 사용된다.
- routes - Flutter에서 routes는 화면과 페이이다.

## 메서드 종류

### push

현재 화면 위에 새 화면을 불러온다.

- push

```dart
@override
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    Navigator.push(context, MaterialPageRoute(builder: (context) => WebViewPage()));
  });
}
```

push와 pushNamed는 기존 페이지 위에 새 화면을 스택처럼 쌓고

- pushNamed

```dart
@override
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    Navigator.of(context).pushNamed('/webView');
  });
}
```

- pushAndRemoveUntil

```dart
void initState() {
super.initState();
Timer(const Duration(seconds:3), () {
Navigator.of(context).pushAndRemoveUntil(MaterialPageRoute(builder: (context) =>
WebViewPage()), (Route<dynamic> route) => false);
});
}
```

### pop

현재 페이지를 날려버리는데, 조금씩 다른 방식으로 동작하는 pop들이 있다.

- pop

```dart
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    Navigator.of(context).pop();
  });
}
```

pop은 현재 페이지를 닫고 더 이상 닫을 페이지가 없는데 pop 메서드가 호출된다면 블랙 스크린이 표시된다. 

- canPop

```dart
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    if (Navigator.canPop(context)) {
      Navigator.of(context).pop();
    } else {
      print('페이지 없음');
    }
  });
}
```

canPop은 날릴 페이지가 있는지 없는지 확인한다. true, falsea로 return한다.

- popAndPushNamed

현재 페이지를 날리고 불러올 페이지를 띄운다

**pushReplacement**

```dart
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    Navigator.pushReplacement(context, MaterialPageRoute(builder: (context) => WebViewPage()));
  });
}
```

현재 화면을 날리고 새 화면을 띄운다.

**pushReplacementNamed**

```dart
void initState() {
  super.initState();
  Timer(const Duration(seconds:3), () {
    Navigator.of(context).pushReplacementNamed('/test');
  });
}
```

현재 화면을 불러올 화면으로 대체한다.