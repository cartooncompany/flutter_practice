- PageView - PageView는 페이지 단위로 스크롤 할 수 있는 화면을 그려준다.
- PageView에 들어가는 페이지들은 모두 뷰포트(viewport) 사이즈로 화면에 보이게 된다.

**뷰포트(ViewPort) - 현재 보고 있는 화면의 영역을 나타낸다. 모바일 뷰포트는 브라우저 창보다 크거나 작고, 상하 좌우로 움직이거나, 더블 탭, 줌인, 줌 아웃을 통해 뷰포트의 배율을 변경할 수 있다.**

예시 코드)

```dart
PageView.builder(
   controller: _controller,
   itemBuilder: (context, index){
     return Container(
       child: Center(
         child: Text(index.toString()),
       ),
     );
   },
   itemCount: null //null로 설정 시 children 개수 무한대.
)
```

- PageView는 PageController를 통하여 컨트롤 된다. 처음 보일 페이지 (initialPage), 각 페이지가 차지하게 될 뷰포트 사이즈 비율(viewportFraction) 등을 설정할 수 있다.

- PageView.builder - 생성자는 사용자에게 보이고 있는 페이지에 대해서ㅈ builder를 호출하므로 children의 개수가 아주 많거나 무한할 경우 유용하게 사용할 수 있다.
- itemcount를 통해 children 개수를 설정할 수 있다.
- PageView - PageView는 페이지 단위로 스크롤 할 수 있는 화면을 그려준다.
- PageView에 들어가는 페이지들은 모두 뷰포트(viewport) 사이즈로 화면에 보이게 된다.