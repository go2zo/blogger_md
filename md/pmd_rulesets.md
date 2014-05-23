---
layout: post
tags: pmd, ruleset
---

## **Java**
Ruleset | 설명
---|---
\* [Android](#android) | 안드로이드 SDK를 다루는 룰들로 구성
[Basic](#java-basic) | 개발자가 적용할만한 좋은 예들로 구성
Braces | 괄호의 배치와 사용에 관한 룰들로 구성
Clone Implementation | clone() 메소드를 사용할 경우 고려해 볼만한 룰들
Code Size | 문제를 발생시킬 수 있는 코드 사이즈 및 복잡성에 관한 룰들
Comments | 코드 주석에 관한 룰들로 구성
Controversial | 어떤 이유이던 논란이 되는 룰들을 포함. custom ruleset을 적절하게 사용 가능. 몇몇이 필요하다고 주장하지만 대부분은 좋아하지 않는 룰들을 포함.
Coupling | 객체들과 패키지들 간의 부적절한 결합(coupling)에 관한 룰들
Design | 클래스 디자인 시 고려할 만한 룰들을 포함
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
Type Resolution | 클래스의  
Unnecessary | 불필요한 코드에 관한 룰들을 포함
Unused Code | 사용되지 않거나 비영향코드를 찾는 룰들을 포함
---|---
※ * 표시는 프레임워크에 dependency한 ruleset

### **Android (Java)** {#android}

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
* CollapsibleIfStatements
* ClassCastExceptionWithToArray
* AvoidDecimalLiteralsInBigDecimalConstructor
* MisplacedNullCheck
* AvoidThreadGroup
* BrokenNullCheck
* BigIntegerInstantiation
* AvoidUsingOctalValues
* AvoidUsingHardCodedIP
* CheckResultSet
* AvoidMultipleUnaryOperators
* ExtendsObject
* AvoidBranchingStatementAsLastInLoop
* DontCallThreadRun
* DontUseFloatTypeForLoopIndices