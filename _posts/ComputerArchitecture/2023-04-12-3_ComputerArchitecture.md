---
date: 2023-04-12 10:07
layout: single
title: "[컴퓨터 구조] L03. Introduction to C, Part 1"
categories:
  - ComputerArchitecture
  - CS
tags:
  - cs61c_"Great Ideas in Computer Architecture"

---

## Compilation

### 특징
- C 컴파일러는 C 프로그램를 아키텍쳐에 특화된 기계언어로 맵핑한다.
	- 자바는 아키텍쳐에 독립적인 bytecode로 변환
	- 파이썬은 코드를 interpret한다.

### C의 컴파일 과정
- .c 파일이 컴파일러에 의해 .o파일(기계어 파일)로 변환되고 .o 파일들이 Linker에 의해 연결되어 최종적으로 .out(실행파일)로 변환된다.
- 만약 foo.c를 수정한다면 foo.c만 다시 컴파일러를 통해 새로운 foo.o 파일을 만들고 기존의 bar.o와 lib.o와 연결해서 a.out을 새로 만든다.

![3.c1](/images/computerarchitecture/3.c1.png)


### 컴파일의 장점
1. 주어진 아키텍쳐에 맞게 최적화해서 기계어를 가지고 있기 때문에 때문에 런타임에서 매우 빠른 성능을 가진다.
2. 수정된 파일들만 다시 컴파일 해주면 되기 때문에 합리적이다. 따라서 큰 파일은 작은 파일로 세분화시키는 것이 일반적이다.(큰 파일은 수정할 때 전체를 다시 컴파일하기 때문에 시간이 오래걸리지만 기능별로 분할된 작은 파일은 수정 시 컴파일하는 시간이 적게 걸리기 때문)

### 컴파일의 단점
1. 컴파일된 파일과 실행파일 모두 프로세서 종류 및 운영체제에 맞게 생성되기 때문에 새로운 시스템에서는 새로 컴파일을 통해 실행파일을 만들어야 한다.
2. "change -> compile -> run" 과정의 반복 때문에 개발 과정을 느릴 수 있다.(코드 수정에 따른 즉각적인 결과를 확인할 수 없다.)

### C Pre-Processor (CPP)
- 컴파일 하기 전에 소스 파일을 처리하는 컴파일러의 한 부분
- \#으로 시작하는 명령어는 C 전처리기 명령어
	- \#include "file.h" : file.h를 삽입
	- \#define PI (3.14150) : 전역변수 설정
	- ...




## C vs Java

| 특징                        | C                                                                                   | Java                                                                                                                   |
| --------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Type of Language            | Function Oriented                                                                   | Object Oriented                                                                                                        |
| Programming Unit            | Function                                                                            | Class = Abstract Data Type                                                                                             |
| Compliation                 | gcc hello.c creates machine language code                                           | javac Hello.java creates Java virtual machine language bytecode                                                        |
| Execution                   | a.out loads and executes program                                                    | java Hello interprets bytecodes                                                                                        |
| hello, world                | \#include <stdio.h></br>int main(void)</br>{</br>printf("Hi\n")</br>return 0;</br>} | public class HelloWorld {</br> public static void</br>main(String[] args) {</br>    System.out.println("Hi");</br>}  } |
| Storage                     | Manual(malloc, free)                                                                | New allocates & initializes,</br>Automatic (garbage collection) frees                                                  |
| Comments                    | /\* ... \*/                                                                         | /\* ... \*/ or // ...                                                                                                  |
| Constants                   | \# define, const                                                                    | final                                                                                                                  |
| Preprocessor                | Yes                                                                                 | No                                                                                                                     |
| Variable declaration        | At beginning of a block                                                             | Before you use it                                                                                                      |
| Variable naming conventions | sum_of_squares                                                                      | sumOfSquares                                                                                                           |
| Accessing a library         | \#include <stdio.h>                                                                 | import java.io.File;                                                                                                                       |


## C Syntax

### main
- 프로그램 실행 시 운영체제에 의해서 가장 먼저 호출되고 return에 의해 종료된다.
- c언어로 작성된 프로그램은 main()함수를 반드시 하나만 가지고 있어야 한다.
- main  함수가 arguments(인수)를 받기 위해 , 다음을 사용한다:
	- int main (int argc, char \*argv[])
	- argc: 메인함수에 전달되는 정보의 개수(how many arguments do you have?)
	- argv: 메인함수에 전달되는 실질적인 정보로, 문자열의 배열


### True or False?
- C에서 False를 표현하는 법
	- 0
	- NULL
	- stdbool.h를 사용해서 false를 거짓으로 나타낼 수 있다.
- C에서 True를 표현하는 법
	- False가 아닌 모든 것


### Type of Variables in C
- 변수의 데이터 타입은 선언되어야하고 변경할 수 없다.
| Type         | Description                              | Example            |
| ------------ | ---------------------------------------- | ------------------ |
| int          | integer numbers                          | 0, -217, 4         |
| unsigned int | unsigned integers                        | 0, 6, 242          |
| float        | floating point decimal                   | 0.0, 3.14, 6.02e23 |
| double       | equal or higher precision floating point | 0.0, 3.142144159   |
| char         | single character                         | 'a', 'D', '\\n'    |
| long         | longer int, 최소 32비트                  | 0, -78,30172097   |
| long long    | Even longer int, 최소 64비트             | 21705192721092512  |

### Integers: Python vs. Java vs. C

| Language | sizeof (int)      |
| -------- | ----------------- |
| Python   | >= 32 bits, infinite |
| Java     | 32 bits           |
| C        | 컴퓨터에 따라 다름; 16 or 32 or 64                  |


### Consts and Enums in C
- Consts(constant)
	- 선언되면 프로그램을 실행하는 동안 값을 바꿀 수 없다.
	- const float golden_ratio = 1.618;
	- const int days_in_week = 7;
- Enums(enumeration)
	- 열거형
	- enum color {RED, GREEN, BLUE};
	- RED는 0, GREEN은 1, BLUE는 2


### Typed Functions in C
- 선언하는 모든 함수에는 return type이 있어야한다. 일반적으로 함수 선언 시 함수 이름 왼쪽에 기대되는 return type이 무엇인지 미리 명시해야한다.
- return type을 void로 설정해서 리턴값이 없는 함수를 만들 수 있다.(근데 void main 은 안됨)
- 함수에 사용되는 값의 데이터 타입도 선언되어야한다.
- 변수와 함수는 사용되기 전에 반드시 선언되어야한다.


### Structs(구조체) in C
- typedef를 통해 새로운 타입을 정의할 수 있다.

```c
typedef unit8_t BYTE;
BYTE b1, b2;
```

- 구조체는 변수의 구조화된 그룹이다.

```c
typedef struct {
	int length_in_seconds;
	int year_recorded;
} SONG;

SONG song1;
song1.length_in_seconds = 213;
song1.year_recorded = 1994;

SONG song2;
song2.length_in_seconds = 248;
song2.year_recorded = 1988;
```

- 약간 파이썬 클래스에서 변수 선언하는거랑 비슷한듯?


### Control Flow

- if-else
	- if (expression) statement;
		- if (x\=\=0) y++;
		- if (x\=\=0) {y++;}
		- if (x\=\=0) {y++; j = j + y;}
	- if (expression) {statement1;} else {statement2;};
	- 웬만하면 괄호를 씌우자
- while
	- while (expression) statement;
	- do statement while (expression);
- for
	- for (initialize; check; update) statement
- switch

```c
swtich (expression){
	case const1: statements
	case const2: statemetns
	defaults: statements
}
break;
```

