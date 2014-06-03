---
layout: post
tags: pmd, ruleset
---

## **Java**
Ruleset | 설명
---|---
\* [Android](#java-android) | 안드로이드 SDK를 다루는 룰들로 구성
[Basic](#java-basic) | 개발자가 적용할만한 좋은 예들로 구성
[Braces](#java-braces) | 괄호의 배치와 사용에 관한 룰들로 구성
Clone Implementation | clone() 메소드를 사용할 경우 고려해 볼만한 룰들
Code Size | 문제를 발생시킬 수 있는 코드 사이즈 및 복잡성에 관한 룰들
Comments | 코드 주석에 관한 룰들로 구성
Controversial | 어떤 이유이던 논란이 되는 룰들을 포함. custom ruleset을 적절하게 사용 가능. 몇몇이 필요하다고 주장하지만 대부분은 좋아하지 않는 룰들을 포함.
Coupling | 객체들과 패키지들 간의 부적절한 결합(coupling)에 관한 룰들
Design | 최적이 아닌 코드구현 플래그 룰들로 다른 방식의 접근을 제안
Empty Code | 빈 구문(method, block statement, try-catch block, ...)을 찾는 룰들
Finalizer | finalizer 사용에 관한 룰들을 포함
Import Statements | import 문에 관한 룰들을 포함
\* J2EE | J2EE 구현에 관한 룰들을 포함
\* Jakarta Commons Logging | 해당 프레임워크 사용에 관한 룰들을 포함
\* JavaBeans | bean 룰을 준수하지 않는 인스턴스들을 잡는 룰들을 포함
\* Java Logging | logger 사용에 관한 룰들을 포함 
\* JUnit | JUnit 테스트에 관한 룰들을 포함
Migration | JDK 버전별 이전에 관한 룰들을 포함. 바로 사용하지 말고 각 버전별 wrapper 룰셋을 사용 (such as migrating_to_13.xml).
Naming | 명명 규칙 이름 및 식별자에 관한 룰들을 포함
Optimization | 성능 향상에 대한 최적화 룰들을 포함
Security Code Guidelines | Sun이 [배포](http://java.sun.com/security/seccodeguide.html#gcg)한 보안 가이드라인을 확인하는 룰들을 포함 
Strict Exceptions | 예외의 throwing/catching에 대한 엄격한 가이드라인을 제공
String and StringBuffer | String, StringBuffer 및 StringBuilder 사용살 발생하는 다양한 문제들에 대한 룰들을 포함
Type Resolution | Java 클래스 타입에 대한 몇몇 룰들
Unnecessary | 불필요한 코드에 관한 룰들을 포함
Unused Code | 사용되지 않거나 비영향코드를 찾는 룰들을 포함
---|---
※ * 표시는 프레임워크에 dependency한 ruleset

### **Android (Java)** {#java-android}

* CallSuperFirst - Super should be called at the start of the method
* CallSuperLast - Super should be called at the end of the method
* DoNotHardCodeSDCard - Use Environment.getExternalStorageDirectory() instead of "/sdcard"

### **Basic (Java)** {#java-basic}

* JumbledIncrementer - 무질서한 반복문 변수(increamenter)는 일반적으로 개발자가 실수 할 수 있으며, 비슷한 다른 변수로 혼동될 수 있다.
* ForLoopShouldBeWhileLoop - 특정 for문은 while문으로 간결하게 만들 수 있다.
* OverrideBothEqualsAndHashcode - 클래스에 equals 메소드(method) 또는 hashCode 메소드를 override할 경우 두 메소드들 모두 override하거나 아니면 모두 하지 않아야 한다. 
* DoubleCheckedLocking - 스레드(thread) 동기화를 위한 코드 중 잘못된 중복 객체 확인은 불완전하게 부분적으로 생성된 객체를 반환할 수 있다.
* ReturnFromFinallyBlock - finally에서는 값을 반환하지 않는다. exception들이 버려질 수 있다.
* UnconditionalIfStatement - 조건절에 비교문이 들어가지 않고 단순히 true 또는 false가 되는 경우 if문을 사용하지 말자.
* BooleanInstantiation - Boolean 객체의 인스턴스화 방지;  new Boolean() 또는  Boolean.valueOf() 로 인스턴스화 할 필요 없이 Boolean.TRUE 또는 Boolean.FALSE로 대체 될 수 있다. 
* CollapsibleIfStatements - 2개의 연속된 조건문은 부울연산자(|| 또는 &&)를 통해 하나의 조건절에 사용될 수 있다.
* ClassCastExceptionWithToArray - List와 같은 collection에서 객체를 array형태로 얻고 싶을 경우 원하는 객체형의 array를 toArray 메소드의 파라메터(parameter)로  전달해야한다. 그렇지 않을 경우 ClassCastException이 발생한다.
* AvoidDecimalLiteralsInBigDecimalConstructor - new BigDecimal(.1)이 .1과 정확하게 같을 것으로 추정할 수 있지만, 하지만 실제로는 .100000000000000005551 1151231257827021181583404541015625과 같다. 그 이유는, .1은 정확하게 double 형으로 표현될 수 없기 때문이다. 그러므로 BigDecimal을 생성할 경우 생성자에 숫자형의 값이 전달될 경우 정확하게 .1이 나올 보장이 없다. 하지만 String형태의 값을 전달할 경우 정확한 BigDecimal을 생성할 수 있으므로, String을 이용하여 BigDecimal을 초기화하자.
* MisplacedNullCheck - 잘못된 위치의 null 체크하는 룰. 기본적으로 변수가 null일 경우 변수를 사용할 경우 NullPointerException이 발생하며, 이 룰은 null 체크가 필요 없거나, 잘못된 null 체크에서 발생한다.
* AvoidThreadGroup - java.lang.ThreadGroup 사용을 피하라. 비록 이것이 스레드 환경에서 사용하도록 의도되었다 하더라도, 이것은 스레드에 안전하지 않은  메소드를 포함한다.
* BrokenNullCheck - || 대신에 &&를 사용하거나 반대로 && 대신에 ||을 사용하여  잘못된 null 체크를 할 경우 NullPointerException이 발생한다.
* BigIntegerInstantiation - 이미 존재하는 다음과 같은 BigInteger 인스턴스들은 생성하지 않는다.  Java 1.2이상: BigInteger.ZERO, BigInteger.ONE; Java 1.5이상: BigInteger.TEN, BigDecimal (BigDecimal.ZERO, BigDecimal,ONE, BigDecimal.TEN)
* AvoidUsingOctalValues - 8진수형 변수값은 사용하지말자. .Java의 8진수 값은  0로 시작하는 integer 값이다.
* AvoidUsingHardCodedIP - 하드 코딩된 IP가 포함된 응용프로그램은 특정 케이스에서 배포가 불가능한 경우가 있다. 그러므로, IP를 코드상 하드코딩하지말자!
* CheckResultSet - ResultSet의 네비게이션 메소드(navication method)들 next, previous, first, last을 사용할 경우 언제나 return 값을 확인해야한다. 실제로, 이런 메소드들이 'false'를 돌려줄 경우, 프로그래머는 이에대한 처리를 해야한다.
* AvoidMultipleUnaryOperators - 복합 단항 연산자 (multiple unary operators)들을 사용할 경우 버그가 발생되거나, 혼란 스럽게 할 수 있다. 이런 사용이 버그가  없도록 확인하거나, 더욱 심플한 표현을 고려해야한다.
* ExtendsObject * - Object를 extends하는 것에 대해 명시할 필요가 없다.
* CheckSkipResult * - skip() 메소드는 요청된 바이트보다 더 적은 수를 건너뛸 수 있다. 이런 경우든 아니든 반환된 값을 확인하라.
* AvoidBranchingStatementAsLastInLoop * - 루프의 마지막 부분으로 분기문을 사용면 버그가 있을 수 있거나 혼란을 야기할 수 있다. 사용이 버그인지 확인하거나 또 다른 접근방법의 사용을 고려하라.
* DontCallThreadRun * - Thread.run()을 명시적으로 호출하면 호출자의 쓰레드에서 실행될 것이다. 대신, 의도했던 행동을 위해 Thread.start()를 호출하라.
* DontUseFloatTypeForLoopIndices * - 루프 인덱스에 대해 부동소수점을 사용하지 마라.  만약 부동소수점을 사용해야 한다면, float가 충분한 정밀도를 제공한다는 것을 확신하고 (공간이나 시간에서) 강력한 성능을 필요로 하는게 아니라면 double을 사용하라.

### **Braces** {#java-braces}

* IfStmtsMustUseBraces - 코드 불록을 둘러싸는 괄호가 없는 if문 사용을 피하라. 코드 서식 또는 들여쓰기로 분실되는 경우는 나머지 제어되는 코드를 분리하기 더 어려워진다.
* WhileLoopsMustUseBraces - While문 역시
* IfElseStmtsMustUseBraces - if..else문 역시 
* ForLoopsMustUseBraces - for문 역시

### **Clone Implementation**

* ProperCloneImplementation - 객체의 clone() 메소드는 super.clone()를 이용하여 implements 해야 한다.
* CloneThrowsCloneNotSupportedException - clone() 메소드는 throws CloneNotSupportedException을 사용해야 한다.
* CloneMethodMustImplementCloneable - clone() 메소드를 구현할 때는 java.lang.Cloneable 인터페이스를 implements해야 한다. 그렇지 않으면 clone() 메소드를 호출할 시에 CloneNotSupportedException을 발생시킨다.