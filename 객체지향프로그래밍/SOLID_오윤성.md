# SOLID 5가지 원리의 핵심 내용

## 단일 책임의 원칙 : SRP(Single Responsibility Principle)

> 작성된 클래스는 **하나의 기능만 가지며 클래스**가 제공하는 모든 서비스는 그 하나의 책임을 수행하는 데 집중되어 있어야 한다는 원칙입니다. 이는 어떤 변화에 의해 클래스를 변경해야 하는 이유는 오직 하나뿐이어야 함을 의미합니다. SRP 원리를 적용하면 무엇보다도 책임 영역이 확실해지기 때문에 한 책임의 변경에서 다른 책임의 변경으로의 연쇄작용에서 자유로울 수 있습니다. 뿐만 아니라 책임을 적절히 분배함으로써 코드의 가독성 향상, 유지보수 용이라는 이점까지 누를 수 있으며 객체지향 원리의 대전제 격인 OCP원리뿐 아니라 다른 원리들을 적용하는 기초가 됩니다. 이 원리는 다른 원리들에 비해서 개념이 비교적 단순하지만, 이 원리를 적용해서 직접 클래스를 설계하기가 그리 쉽지만은 않습니다. 왜냐하면, 실무의 프로세스는 매우 복잡 다양하고 변경 또한 빈번하기 때문에 경험이 많지 않거나 도메인에 대한 업무 이해가 부족하면 나도 모르게 SRP원리에서 멀어져 버리게 됩니다. 따라서 평소에 많은 연습과 경험이 필요한 원칙입니다.
> 

### 한 줄 요약 : 모든 클래스는 각각 하나의 책임만 가져야 하는 원칙

예를 들어 A라는 로직이 존재한다면 어떠한 클래스는 A에 관한 클래스어야 하고 이를 수정한다고 했을 때도 A와 관련된 수정이어야 합니다 .

처음부터 단일 책임 원칙을 지키는 클래스를 만드는 것이 가장 좋겠지만, 이미 작성된 클래스의 책임이 여러 개라고 생각되면 리팩토링을 통해 책임의 개수만큼 클래스를 나누는 것도 좋은 방법입니다. 

### 적용이슈

- 클래스는 자신의 이름이 나타내는 일을 해야 합니다. 올바른 클래스 이름은 해당 클래스의 책임을 나타낼 수 있는 가장 좋은 방법입니다.
    
    각 클래스는 하나의 개념을 나타내어야 합니다. 
    
    사용되지 않는 속성이 결정적 증거입니다.
    
    무조건 책임을 분리한다고 SRP가 적용되는 건 아닙니다. 각 객체 간의 응집력이 있다면 병합이 순 작용의 수단이 되고 결합력이 있다면 분리가 순 작용의 수단이 됩니다. 
    

- 모든 책임을 하나의 클래스로 잘게 나누는 것은 꼭 좋은 것은 아닙니다  시스템의 변동이 거의 없는 경우에는 하나의 클래스에 둘 이상의 책임이 있어도 괜찮은 경우가 있습니다. 이러한 경우에는 오히려 책임을 나누게 되면 클래스의 숫자가 많아져 코드의 복잡성이 올라가는 단점이 생기게 됩니다.
    
    따라서 상황에 맞게 단일 책임 원칙을 적용하는 것이 좋습니다. 
    

```kotlin
fun add(num1: Int, num2: Int): Int {
    return num1 + num2
}

fun numPrint(num: Int) {
    print(num)
}

fun addPrint(num1: Int, num2: Int) {
    val num = num1 + num2
    print(num)
}
```

굳이 함수의 수를 줄이기 위해 함수를 합칠 필요는 없습니다.

```kotlin
class Cat() {
    val age: Int? = null
    val name: String? = null

    fun eat(food: String) {}
    fun walk() {}
    fun speak() {}

    fun print() {
        print("age : $age name: $name")
    }

    fun log() {
        Log.d("Cat", "age : $age name: $name")
    }
}
```

먹기, 걷기, 말하기는 일반적으로 아는 고양이의 기능입니다.

하지만 프린트, 로그는 고양이의 기능이 아닙니다. 

단일책임원칙에 위배됩니다. 

이러한 경우 고양이 클래스에서 프린트와 로그를 빼주어야 합니다. 

```kotlin
class Cat() {
    val age: Int? = null
    val name: String? = null

    fun eat(food: String) {}
    fun walk() {}
    fun speak() {}

    fun state(): String {
        return "age : $age name: $name"
    }

    //    fun print() {
//        print("age : $age name: $name")
//    }
//
//    fun log() {
//        Log.d("Cat", "age : $age name: $name")
//    }
}

fun main() {
    val kitty = Cat()
    print(kitty.state())
    Log.d(kitty.state())
}
```

고양이 클래스에서 프린트와 로그는 삭제하는 대신 두개의 기능을 구현해야하는데, 고양이의 상태를 구현하는 함수를 만들어줍니다. 

고양이를 사용하는 클라이언트 코드에서는 그 상태를 리턴해주는 state()함수를 가져와 프린트해주거나 로그를 남기는 방법을 사용할 수 있습니다.

이러한 방식으로 수정을하면 고양이 클래스에는 고양이와 관련된 함수만 남게됩니다. 

단일책임원칙을 준수할 수 있습니다. 

## Open-Closed

확장에 대해서는 개방 수정에 대해서는 폐쇄라는 뜻인데 전혀 감이 오지 않습니다. 

코드에 대한 제한이 아니라 코드 행동에대한 원칙이기 때문에 이해가 바로 와닫지 않습니다. 예제를 보시면 어느정도 감이 오실겁니다. 

먼저 개방폐쇄원칙을 준수하지 않은 코드를 보면,

```kotlin
class Animal(type: String) {
    val a_type: String = type
}

fun hey(animal: Animal) {
    when (animal.a_type) {
        "Cat" -> {
            print("meow")
        }
        "Dog" -> {
            print("bark")
        }
        else -> {
						// Error!
        }
    }
}

fun main() {
    val kitty = Animal("Cat")
    val toto = Animal("Dog")
		// 소와 양을 추가 
		val cow = Animal("Cow")
    val sheep = Animal("Sheep")

    hey(kitty)
    hey(toto)
}
```

현재 두마리의 동물이 있을 때, 다른 동물을 추가하려고하면 에러가 발생하게됩니다.

동물의 범주안에는 고양이와 강아지가 있는데 양과 소에 대해서 확장(extention)하려고하면 hey() 함수까지 수정해야하는 상황이 발생합니다.

이는 개방폐쇄원칙에 위배됩니다.

어떻게 해결할 수 있을까?

1. interface class
2. abstract class

를 사용하면 됩니다.

아래는 개방폐쇄원칙을 만족하는 코드입니다.

```kotlin
open class Animal2 {
    open fun speak() {}
}

class Cat : Animal2() {
    override fun speak() {
        print("meow")
    }
}

class Dog : Animal2() {
    override fun speak() {
        print("bark")
    }
}

fun hey2(animal: Animal2) {
    animal.speak()
}

fun main() {
    val kitty = Cat()
    val toto = Dog()
    hey2(kitty)
    hey2(toto)
}
```

위 코드에서 소와 양을 추가를 해야하는 상황일 때 개방폐쇄원칙을 잘 준수한 코드라면 소와양에 대한 확장은 자유롭게하고 hey() 함수는 수정에 대해 폐쇄되어있기 때문에 수정을 할 필요가 없습니다. 

```kotlin
open class Animal2 {
    open fun speak() {}
}

class Cat : Animal2() {
    override fun speak() {
        println("meow")
    }
}

class Dog : Animal2() {
    override fun speak() {
        println("bark")
    }
}

class Sheep : Animal2() {
    override fun speak() {
        println("meh")
    }
}

fun hey2(animal: Animal2) {
    animal.speak()
}

fun main() {
    val kitty = Cat()
    val toto = Dog()
    val sheep = Sheep()
    hey2(kitty)
    hey2(toto)
    hey2(sheep)
}
```

hey 함수 수정없이 다른 동물들을 부를 수 있습니다. 

클래스 구조를 animal을 인터페이스로 가지고 그를 상속받는 고양이 강아지 양 소를 가짐으로써 확장에 대해서 열려있고 수정에 대해서 닫혀있는 코드 구조를 가질 수 있습니다. 

이러한 클래스 구조를 갖는다면 100개 1000개 동물을 추가해도 매번 hey() 함수를 수정할 필요가 없습니다.

이것이 바로 개방폐쇄원칙입니다. 

## 리스코브 치환 원칙 : LSP(Liskov Substitution Principle)

type S가 T의 Sub Type일 때 Object T는 Object S로 치환가능합니다. 

내 생각 : 부모 타입은 자식 타입으로 치환이 가능하다 라는 말 같음

타입 T가 있고 그의 Sub타입인 S1,S2,S3가 있을 때 Object T는 그 Sub Type의 Object들 S1,S2,S3로 바꾸어도 우리가 생각했던대로 프로그램이 동작해야한다라는 말입니다.

Cat Type

Black Cat, Stray cat

Cat를 Black, Stray로 치환해도 전체적인 프로그램은 우리가 원하는대로 돌아간다. 

아래 예시 코드를 확인해보자 

```kotlin
open class Squirrel() {
    open fun speak() {
        println("jjack")
    }
}

class BlackSquirrel() : Squirrel() {
    override fun speak() {
        println("black jjack")
    }
}

class PinkSquirrel() : Squirrel() {
    override fun speak() {
        println("Pink jjack")
    }
}

fun speak(squirrel: Squirrel) {
    squirrel.speak()
}

fun main() {
    val squirrel = Squirrel()
    val blackSquirrel = BlackSquirrel()
    speak(squirrel = squirrel)
    speak(squirrel = blackSquirrel)
}
```

다람쥐가 우는 소리를 출력하는 speak() 함수에 부모 타입인 Squirrel을 넣으면 “jjack” 을 출력합니다. 이때 자식 타입인 BlackSquirrel or PinkSquirrel을 넣어도 우리가 원하는대로 프로그램은 돌아갑니다.

그런데 여기서 기획자가 Fish 클래스를 넣어달라는 요청이 들어왔을 때 생선은 아무소리도 낼 수 없으니까 예외를 던지도록 코드를 작성할 것입니다.   

```kotlin
open class Squirrel() {
    open fun speak() {
        println("jjack")
    }
}

class BlackSquirrel() : Squirrel() {
    override fun speak() {
        println("black jjack")
    }
}

class PinkSquirrel() : Squirrel() {
    override fun speak() {
        println("Pink jjack")
    }
}

fun speak(squirrel: Squirrel) {
    squirrel.speak()
}

class Fish() : Squirrel() {
    override fun speak() {
        throw Exception("Fish can not speak")
    }
}

fun main() {
    var squirrel = Squirrel()
    val blackSquirrel = BlackSquirrel()
    speak(squirrel = squirrel)
    speak(squirrel = blackSquirrel)

    squirrel = Fish()
    speak(squirrel=squirrel)
}
```

다람쥐에 생선을 넣는다 라는 것은 다람쥐를 생선으로 치환도 할 수 없고 리스코프 치환원칙을 위배하는 코드가 됩니다. 

이를 해결하기 위해서 처음부터 전체적인 클래스 구조를 제대로 다람쥐와 생선을 생각하고 만들거나 이러한 문제가 발생하지 않도록 다른 방법을 사용하도록 해야합니다. 

그만큼 코드가 복잡해지게 됩니다. 

## 인터페이스 분리 원칙 : ISP(Interface Segregation Principle)

> 클라이언트들은 사용하지 않을 메서드들에 의존하게 해서는 안됩니다. 큰 인터페이스들은 더 작은 인터페이스로 분리하는 것이 좋다라는말 입니다.
> 

 

```kotlin
//수륙양용 자동차
interface ICarBoat{
    fun drive()
    fun turnLeft()
    fun turnRight()

    fun steer()
    fun steerLeft()
    fun steerRight()
}

class Tico :ICarBoat{
    override fun drive() {
				// 자동차 앞으로 가기
    }

    override fun turnLeft() {
				// 자동차 왼쪽으로 돌기
    }

    override fun turnRight() {
				// 자동차 오른쪽으로 돌기
    }

    override fun steer() {
				// 배 앞으로 가기
    }

    override fun steerLeft() {
				// 배 왼쪽으로 돌기
    }

    override fun steerRight() {
				// 배 오른쪽으로 돌기
    }

}
```

너무 큰 인터페이스를 만들게되면 그 안에 자동차, 보트의 인터페이스들이 모두 들어가게 됩니다. 

ICarBoat 인터페이스를 받아 자동차와 보트를 각각 만들게 되면

그 안에는 인터페이스에 있는 모든 함수들이 같이 들어오게 됩니다. 

이 중에서 자동자는 보트에 대한 기능이 필요가 없고, 보트에는 자동차에 대한 기능이 필요가 없습니다. 

여기서 인터페이스 분리 원칙에서 말하고자 하는 것은 

이렇게 큰 인터페이스를 가져갈 것이 아니라 이를 분리해서 더 작은 인터페이스들을 가지라는 뜻입니다. 

ICar, IBoat 인터페이스를 따로 가지라는 것입니다. 

그 내부에는 각각 맞는 인터페이스들이 들어갑니다. 

이렇게 분리해서 구성하게되면 자동차가 필요할 때 자동차 인터페이스만 가져오면 되고 배를 만들때는 보트 인터페이스만 가져와서 클래스를 만들면 됩니다. 

아주 특이하게 수륙양용 자동차를 만들어야할 때는 두개의 인터페이스를 조합해서 클래스를 만들면 됩니다. 

```kotlin
interface ICar {
    fun drive()
    fun turnLeft()
    fun turnRight()
}

interface IBoat {
    fun steer()
    fun steerLeft()
    fun steerRight()
}

class CarBoat : ICar, IBoat {
    override fun drive() {
				// 자동차 앞으로 가기
    }

    override fun turnLeft() {
				// 자동차 왼쪽으로 돌기
    }

    override fun turnRight() {
				// 자동차 오른쪽으로 돌기
    }

    override fun steer() {
				// 배 앞으로 가기
    }

    override fun steerLeft() {
				// 배 왼쪽으로 돌기
    }

    override fun steerRight() {
				// 배 오른쪽으로 돌기
    }
}
```

## 의존 역전 법직 : DIP(Dependency Inversion Principle)

전통적인 방식으로 클래스를 구성할 때

동물원 안에 고양이와 강아지를 넣을 때 

코드 디펜던시로 나타낼 떄

동물원은 고양이와 강아지의 디펜던시를 가지고 있습니다. 

그리고 여기서 동물원은 더 많은 정보를 갖고 있기 때문에 high level 모듈로 볼 수 있고 고양이와 강아지는 Low Level로 볼 수 있습니다. 

고양이와 강아지 클래스를 만들어보겠습니다. 

이어서 동물원 클래스를 만든다면, 고양이와 강아지를 가지고 있습니다. 

즉, 동물원은 고양이와 강아지의 디펜던시를 가지고 있습니다. 

high level모듈들이 low레벨 모듈들을 가지고 있는 것은 자연스럽다. 

이후 동물원에 양과 소를 추가해 줄 때 

동물원은 디펜던시가 추가됩니다. 

이렇게 하위레벨 모듈들의 디펜던시가 증가하게되면 나중에 유지보수가 어렵게됩니다. 이를 해결하기 위해 의존역전법칙을 사용합니다. 

동물원 → 동물 ← Cat,Dog, Cow, Sheep, 등등등

 

```kotlin
open class Animal3 {
    open fun speak() {}
}

class Dolphin : Animal3() {
    override fun speak() {
        println("wi~~~~~ng")
    }
}

class Monkey : Animal3() {
    override fun speak() {
        println("ou kiki")
    }
}

class Zoo {
    val animals = mutableListOf<Animal3>()

    fun addAnimal(animal3: Animal3) {
        animals.add(animal3)
    }

    fun speakAll() {
        animals.forEach {
            it.speak()
        }
    }
}

fun main() {
    val zoo = Zoo()
    zoo.addAnimal(Dolphin())
    zoo.addAnimal(Monkey())
    zoo.speakAll()
}
```

클라이언트 코드에서는 동물원을 만들고 각 동물들을 넣어줍니다. 

이처럼 high level 모듈인 동물원이 low level 모듈들인 동물들에 대한 직접적인 디펜던시를 가지지않고 추상레이어인 동물에 디펜던시를 가지게되면 즉, 의존역전구조를 갖게되면 나중에 다른 동물이 추가되더라도 동물원은 전혀 건들 필요가 없습니다.

기존에 전통적인 의존 순서 High Level 모듈에서 Low Level 모듈들을 의존하게 만드는 것이 아니라 

추상화 모듈을 하나 만들어서 high Level 모듈도 Low Level 모듈도 추상화 클래스에 의존하게 만드는 것 

그 과정에서 화살표의 방향이 바뀌기 때문에 의존역전이라고 합니다. 

Zoo → Cat,Dog,,,, 

Zoo → Animal ← Cat, Dog