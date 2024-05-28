# Column과 Row의 차이

- **Row**는 **가로를 주축**으로 함
- **Column**은 **세로를 주축**으로 함

---

### 정렬 방식

**MainAxisAlignment.center**

- Row - 가로축을 기준으로 가운데 정렬한다
- Column - 세로축을 기준으로 가운데 정렬한다.

**MainAxisAlignment.start**

- Row - 가로축을 기준으로 왼쪽 정렬한다
- Column - 세로축을 기준으로 위쪽 정렬한다.

**MainAxisAlignment.end**

- Row - 가로축을 기준으로 오른쪽 정렬한다
- Column - 세로축을 기준으로 아래쪽 정렬한다.

**MainAxisAlignment.spaceEvently**

- child widget 사이의 여유 공간을 모두 균등하게 배분함

**MainAxisAlignment.spaceBetween**

- child widget을 시작과 끝에 배치하고 이 사이에 나머지 child widget을 배치
- 시작과 끝 사이의 위젯의 나머지 공간은 모두 균일하게 배분함

**MainAxisAlignment.spaceAround**

- 첫 번째와 마지막 child 앞뒤에 여유 공간을 나머지 child와 공간의 절반만큼 배치함

---

**CrossAxisAlignment.center**

- Row - 가로축을 기준으로 가운데 정렬
- Column - 세로축을 기준으로 가운데로 정렬

**CrossAxisAlignment.start**

- Row - 가로축을 기준으로 위쪽 정렬
- Column - 세로축을 기준으로 왼쪽 정렬

**CrossAxisAlignment.end**

- Row - 가로축을 기준으로 아래쪽 정렬
- Column - 세로축을 기준으로 오른쪽 정렬

**CrossAxisAlignment.stretch**

- 좌우를 꽉 차게 배치

**CrossAxisAlignment.baseline**

- Row - 수평 정렬
- Column - 수직 정렬

---

**TextBaseline.alphabetic**

- 알파벳 기준선이고, 영어와 같은 알파벳 문자가 기준이 됨

**TextBaseline.ideographic**

- 기준선은 텍스트 영역의 맨 아래에 있다.

---

### MainAxisSize

- **Column의 사이즈를 지정**
- **MainAxisSize.min -** 자식 위젯들 만큼의 사이즈로 최소화 시킴
- **MainAxisSize.max -** 자식 위젯들 과는 상관 없이 가능한 한 최대의 사이즈로 변경됨