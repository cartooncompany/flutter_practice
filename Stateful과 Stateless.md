## **stateful과 stateless**

### StatelessWidget

- UI에 영향을 미치는 데이터가 없으면? 데이터의 변동에 따라 모양이 변하지 않는다는 말. 즉, 모양이 고정된 widget이 됨
- 한번 그려지고 나면 데이터가 어떻게 변하던지, 이 위젯에는 아무런 영향이 없다.

### StatefulWidget

- UI에 영향을 미치는 데이터가 있으니, 그 데이터가 변함에 따라 UI가 변하게 된다.
- setState()란 함수를 사용해 State의 변화를 알려줘야함
- setState()함수가 실행되면 바뀐 데이터를 체크해 해당 데이터로 위젯을 다시 그린다.
- 결과적으로 State가 변하면 UI가 변하면 위젯, 이게 바로 StatefulWidget이다.