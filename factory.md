## Factory Pattern

---

Factory는 싱글톤 패턴을 기반으로 새로운 인스턴스를 만들지 않을 때 사용하는 생성자입니다. 이미 생성된 인스턴스가 있다면 생성하지 않고 return해서 재사용하고, 싱글톤 개념에 따라 단 한 개의 인스턴스만 생성합니다. 그러기 위해서는 싱글톤 패턴에 대해서 알 필요가 있습니다.

## Singleton Pattern

---

객체 단 하나 만을 생성한 뒤 이를 어느 곳에서든지 이 생성된 단 하나의 객체를 참조할 수 있게 해주는 패턴입니다. 

장점

- 메모리 낭비를 줄일 수 있다.
- 성능적인 부분에서 도움을 준다.
- 공유도 비교적 쉽게 할 수 있다.

이제 아래에 있는 예제를 통해 팩토리에 대해 알아봅시다.

**step 1.**  enum형식으로 PersonJob을 선언해줍니다**.**

```dart
enum PersonJob {
  student,

  developer,
}
```

enum은 열거형이란 뜻으로, 분류를 쉽게 할 수 있도록 도와주며, switch구문과 어울리는 문법입니다.

step2. abstract(추상) Person 클래스를 선언하고 getName과 getJobName을 각각 String값으로 return할 수 있는 매소드를 선언해줍니다.

```dart
abstract class Person {
  String getName();

  String getJobName();
}
```

이 추상 클래스는 하위 클래스가 implements하게 되어서 추상 클래스에서 선언된 매소드를 재정의 하게 됩니다. 추상 클래스에 선언된 메소드는 말그대로 메소드의 이름과 타입만 정의해주는 것입니다.

step 3. Student 클래스를 다음처럼 정의해줍니다.

```dart
class Student implements Person {
  final String name = "Andrew";

  final String jobName = "High School Student";

  @override
  String getName() {
    return name;
  }

  @override
  String getJobName() {
    return jobName;
  }
}

```

step 4. Developer도 똑같이 정의해줍니다.

```dart
class Developer implements Person {
  final String name = "John";

  final String jobName = "Frontend Developer";

  @override
  String getName() {
    return name;
  }

  @override
  String getJobName() {
    return jobName;
  }
}
```

step 5. Factory부분도 추가해줍니다.

```dart
abstract class Person {
  String getName();

  String getJobName();

  factory Person(PersonJob job) {
    switch (job) {
      case PersonJob.student:
        return Student();

      case PersonJob.developer:
        return Developer();
    }
  }
}

```

여기에서는 반드시 Person 클래스를 implements하는 클래스로 return 해야 합니다.

step 6. main함수를 작성해줍니다.

```dart
void main() {
  print("Person 1: ${Person(PersonJob.student).getJobName()}");

  print("Person 2: ${Person(PersonJob.developer).getJobName()}");
}
```

결과물

```dart
Person 1: High School Student
Person 2: Frontend Developer
```

전체코드

```dart

enum PersonJob {
  student,
  developer,
}

abstract class Person {
  String getName();

  String getJobName();

  factory Person(PersonJob job) {
    switch (job) {
      case PersonJob.student:
        return Student();

      case PersonJob.developer:
        return Developer();
    }
  }
}

class Student implements Person {
  final String name = "Andrew";

  final String jobName = "High School Student";

  @override
  String getName() {
    return name;
  }

  @override
  String getJobName() {
    return jobName;
  }
}

class Developer implements Person {
  final String name = "John";

  final String jobName = "Frontend Developer";

  @override
  String getName() {
    return name;
  }

  @override
  String getJobName() {
    return jobName;
  }
}

void main() {
  print("Person 1: ${Person(PersonJob.student).getJobName()}");

  print("Person 2: ${Person(PersonJob.developer).getJobName()}");
}
```