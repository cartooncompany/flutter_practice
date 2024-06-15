### ListView와 ListView.builder

**공통점** 

- 스크롤이 가능한 배열 형 위젯이라는 점

**다른 점**

- ListView - 리스트 뷰 안에 모든 child를 생성해서 보여준다.
- LIstView.builder - 그때그때 필요한 만큼만 데이터를 저장소나 서버에서 불러온다는 것이 차이점이다.

예시 코드)

```dart
ListView.builder(
          itemCount: 100,
          itemBuilder: (context, index) {
            return Text("${index}");
          },
          
      ),
```

이 위젯에는 몇 개의 항목을 만들 것이고, 몇 번째 항목에는 어떤 view를 그려줄 것인지 말해주어야 한다.

- itemCount: int값이며, ListView 항목들의 총 개수에 해당한다. (단, 주어지지 않으면 무한히 만들어진다.)
- itemBuilder: index번째에 해당하는 view를 그려주는 함수이다.(단, index는 0부터 시작함)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/61237269-d220-4545-96b5-6d20b19edc38/950fa7ab-facf-469c-99bb-877026b0efa4/Untitled.png)

이 외에도 

- reverse: true,를 사용하여 역순으로 출력할 수 있다.
- scrollDirection에서 Axis.horizontal으로 설정하여 가로로 스크롤이 가능하도록 만들 수 있다

### ListView.seperated

- ListView.builder에서 구분선이 필요할 때 사용한다.

예시 코드)

```dart
ListView.separated(
          itemBuilder: (context, index) {
            return Text("${index}");
          },
          separatorBuilder: (context, index) => const Divider(),
          itemCount: 100,
      ),
```

- itemBuilder와 itemCount는 위에 있는 ListView.builder와 동일하다.
- separatorBuilder: index번째에 구분선을 어떤 View에 그려줄지 결정하는 함수이다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/61237269-d220-4545-96b5-6d20b19edc38/0f17f13c-8747-42d5-a567-e6f010eced2b/Untitled.png)