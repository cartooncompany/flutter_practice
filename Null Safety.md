## Null Safety

**Null Safety -** Null-Safety에 대해 꼭 기억해야 할 세 가지가 있다

1. 모든 변수는 null이 될 수 없으며, non-nullable변수에는 null값을 할당할 수 없다.
2. non-nullable 변수를 위한 null check가 필요 없음
3. “Class 내의 변수는”반드시 선언과 동시에 초기화를 시켜야 함

### Null Safety 사용법

1. **Type뒤에 물음표를 붙여준다.**

```dart
class Person{
					String? name;
					
			String nameChange(String? name) {
					this.name = name;
					return name.toUpperCase();
			}
}
```

이런 코드를 작성하여도 return 되는 name이 null이면 toUpperCase를 실행할 수 없다는 에러가 뜬다.

이는 null 체크를 추가해 이를 해결할 수 있다.

```dart
class Person {
				String? name;
				
		String nameChange(String? name) {
				this.name = name;
				if(name == null) {
					return 'need a name';
				} else{
					return name.toUpperCase();
				}
		}
}
```

1. **선언을 먼저하고 나중에 할당한다.**

```dart
class Person{
				late int age;
				
		int sum(int age, int num) {
		this.age = age;
		int total = age + num;
		
		return total + age;
		}
}

void main() {
	Person p = Person();
	print(p.sum(100, 50)):
}
```

선언과 동시에 변수 값이 할당되는 것이 아니라 나중에 할당이 되어야 하는 경우에는 변수의 type앞에 late를 붙인다.

1. **nullable 변수가 항상 non-nullable 변수 값을 가진다는 확신이 있으면 nullable변수에 느낌표를 추가한다.**

```dart
void main(){
	int x = 50;
	int? y;
	if(x > 0) {
		y = x;
	}
	int value = y;
	print(value);
}
```

이런 경우, nullable value값인 y는 non-nullable value값인 value에 할당될 수 없다는 오류가 뜬다.

nullable value값인 y가 항상 non-nullable 값을 가질 것이라고 알려줄 수 있다.

!(느낌표, Exclamation or Bang)를 추가해주면 문제가 사라진다.

```dart
void main(){
	int x = 50;
	int? y;
	if(x > 0) {
		y = x;
	}
	int value = y!;
	print(value);
}
```

1. **required 추가하기**

```dart
void main() {
	print(add());
}
int add({int a, int b}) {
	int sum = a + b;
	return sum;
}
```

named argument 형식의 인자 값은 optional하기 때문에 아무 값도 전달하지 않을 수 있다.

따라서 null safety 오류가 발생한다.

이럴 때에는 required를 type앞에 추가해주면 된다.

```dart
void main() {
	print(add());
}
int add({required int a, required int b}) {
	int sum = a + b;
	return sum;
}
```

add메서드에서 두 개의 인자값 중 하나의 인자값만 전달해주거나, 둘 중 하나라도 null이 전달되면 컴파일 에러가 발생한다.

하나의 값이 null일 경우에는 그 값에 대한 null-check를 추가해야 한다.

```dart
void main(){
	print(add(a: Null, b: 5));
}
int add({required int a, required int b}) {
	if(a == null) {
		return b;
	}
	int sum = a + b;
	return sum;
}
```